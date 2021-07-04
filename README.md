# PlasmoPlots
```julia
using Plasmo
using Plots, PlasmoPlots
gr()

#create an optigraph
graph = OptiGraph()

@optinode(graph1,n1)
@variable(n1, y >= 2)
@variable(n1,x >= 0)
@constraint(n1,x + y >= 3)
@objective(n1, Min, y)

@optinode(graph1,n2)
@variable(n2, y)
@variable(n2,x >= 0)
@constraint(n2,x + y >= 3)
@objective(n2, Min, y)

@optinode(graph1,n3)
@variable(n3, y )
@variable(n3,x >= 0)
@constraint(n3,x + y >= 3)
@objective(n3, Min, y)

@linkconstraint(graph1, n1[:x] + n2[:x] + n3[:x] == 3)

#plot the graph layout
plt_graph1 = layout_plot(graph1,node_labels = true,markersize = 60,labelsize = 30,
linewidth = 4,layout_options = Dict(:tol => 0.01,:iterations => 2));

#plot the matrix layout
plt_matrix1 = matrix_plot(graph1,node_labels = true,markersize = 30);
```
