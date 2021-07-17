# Sequence Types

In Python Sequences refer to ordered group of items. These include Lists, Tuples and Strings. Some of the operations that sequences support include:

1. Concatenation
2. Repetitions
3. "in" and "not in" operators
4. Element wise indexing/Slicing.

It is important to note that all Sequences are "iterable" but it is not necessary that all iterables are sequences. E.g: Unordered Sets vs Lists. Further, **range ** objects are additionally restrictive as they don't permit concatenation/reptition.

```
Sample:
s = (0,1,2) 
list_s = [0,2.9, 30]
set_s = {0,2,3} ### Sets are not subscriptable
print(s[0], list_s[0]) ### Works fine
try:
    print(set_s[0]) ### Throws Type error: 'set' object is not subscriptable
except TypeError as e:
    print(e)

```



## TASKS

### Create a polygon class that is strictly convex and that has the following characteristics:

1. all interior angles are less than 180

2. all sides have equal length

3. where initializer takes in:

   1. number of edges/vertices
   2. circumradius

4. that can provide these properties:

   1. \# edges
   2. \# vertices
   3. interior angle
   4. edge length
   5. apothem
   6. area
   7. perimeter

5. that has these functionalities:

   1. a proper `__repr__ `function
   2.  equality function
   3. greater than functionality


### Solution

```
class ConvexPolygon():
    ''' 
    A regular strictly convex polygon is a polygon that has the following characteristics:
        all interior angles are less than 180
        all sides have equal length
    '''
```

This is the primary class  whose `__init__` function takes two arguments the number of edges and the circumradius. Basic checks are enforced  i.e the datatypes must numerical and number of edges must not be less than 3. Following is the list of properties supported by the class.

```
    @property
    def get_vertices(self):
        '''
        Property: number of vertices of the polygon
        '''
    @property
    def get_edges(self):
        '''
        Property: number of edges of the polygon
        return self._n_sides    
    @property
    def get_circumradius(self):
        '''
        Property: circumradius of the polygon
        '''
    @property
    def get_interior_angle(self):
        '''
        Property: number of interior angles of the polygon
        '''
    @property
    def get_length_of_side(self):
        '''
        Property: length of one side of the polygon
        '''
    @property
    def get_apothem(self):
        ''''
        Property: Length of apothem of the polygon
        '''
    @property
    def get_area(self):
        ''''
        Property: Area of the polygon
        '''        
    @property
    def get_perimeter(self):
        '''
        Property: Perimeter of the polygon
        '''
```

The ConvexPolygon class also provides the comparison functions i.e `__gt__` and `__eq__`. The criteria for comparison is below:

1. equality (==): when number of edges and the circumradius is equal numerically for both the objects
2. '>' comparison is implemented based on number of edges/vertices only.

```
    def __eq__(self, rhs_poly):
        '''
        Implementation of equality function for ConvexPolygon class.
        Returns True when both circumradius and the number of sides both match.
        '''
    def __gt__(self, rhs_poly):
        '''
        Implementation of greater than function for ConvexPolygon class.
        Returns True when LHS has greater number of vertices/sides than RHS.
        '''
```

### Implement a Custom Polygon sequence type

1. Implement a Custom Polygon sequence type:
   1. where initializer takes in:
      1. number of vertices for largest polygon in the sequence
      2. common circumradius for all polygons
   2. that can provide these properties:
      1. max efficiency polygon: returns the Polygon with the highest **area to perimeter** ratio
   3. that has these functionalities:
      1. functions as a sequence type (`__getitem__`)
      2. supports the len() function (`__len__`)
      3. has a proper representation (`__repr__`)

### Solution

```
class PolygonSequences():
    '''
    Polygon sequence class that generates all polygons for a given circumradius and upto the max edges specified by n_sides.
    E.g: If input radius = 4 and n_sides = 10, polygons starting from sides = 3,4,...10 of size 4 will be generated
    Returns sequence of ConvexPolygon class.
    '''
```

This is the primary class  whose `__init__` function takes two arguments the number of edges and the circumradius. Here number of edges will be used to generate a sequence of all the ConvexPolygon objects between 3 and number of max edges. Each object will have ofcourse use the same circumradius. To support indexing and slicing, `__getitem__` method is explicitly implemented. 

```
    def __getitem__(self, s):
        '''
        Allows for proper iteration of the sequence.
        '''
     
```

Another important function that is implemented is the `get_max_efficiency_poly`. This function returns the polygon with the maximum ratio of area to perimeter amongst all the polygons in the sequence.

```
    def get_max_efficiency_poly(self):
        '''
        Returns the max efficient polygon. We can make a simple hack to use the one with largest number of edges.
        '''
```



## User Details:
Submitted by: Rajesh Y(github: rajy4683)
Email ID: st.hazard@gmail.com
