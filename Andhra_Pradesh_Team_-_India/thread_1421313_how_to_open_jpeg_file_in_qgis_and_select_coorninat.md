---
title: "how to open jpeg file in qgis and select coorninates"
date: 2010-03-04
forum: Andhra Pradesh Team - India
---

### Post by bharath1234 on 2010-03-04
hello
i have installed qgis i want to open jpeg file in it...though i had open jpeg file in qgis iam unable to give coordinates to 4 points...

---

### Post by Herman on 2010-03-15
1. First you need to pick out at least three or four objects which you can see clearly in your .jpeg map and also in the map you already have open in Quantum GIS.
If you have no other map already open in Quantum GIS you can use google earth instead, to get the coodinates for three or four distinct landmarks which show in your .jpeg raster.
Another way to find the coordinates for your control points is to go and visit those locations with a GPS unit and record the Y and X coordinates yourself.

These three or four, (or more if you like) objects are called 'control points', and it's best if they are close to the corners of your raster, one can be in the middle if you want, as long as they are well spread out, not too close together if you want good results.

You should try to choose things you know have not been moved, like a mountain top. If you choose something like a bridge, be careful that the bridge has not been rebuilt in another nearby spot since your .jpeg map was made. That would put your map's alignment out.

---

### Post by Herman on 2010-03-15
3. in Quantum, click 'Plugins'-->'Georeferencer'-->'Georeferencer'

4. In the 'Georeferencer' dialog window, type or paste the path and name of your file in the 'Raster File:' field, or use the 'Find' button and navigate to your file and select it.

5. Your image should appear in the 'Reference Points' dialog window, and you can zoom in and pan around in that image very easily and quickly to find your control points. 
Find each of your control points one at a time and click on the 'Add Point' button, (looks like a dice), and click on a control point.
The 'Enter Map Co-ordinates' dialog window appears and you can enter your co-ordinates in the x and y fields, or else click the 'From Map Canvas' button and locate your points on the map, (slow and tedious).

6. Repeat the above for at least two more control points, more is better.

7. When done, click 'Create and Load Layer'.

8. In Quantum's 'Legend' pane, right-click on your new layer and click 'zoom to layer extent', to see what it looks like. Look around the edges of your new layer and see if rivers and roads line up with the rivers and roads in the control layer.

9. In Quantum's 'Legend' pane, right-click on your new layer and click 'Properties', and click the 'transparency' tab. Set the transparency to around 50%. Hit 'Apply', and wait, then 'OK'.
Now, zoom in and pan around and see if your alignment is right or not.

10. If you are happy with your alignment, click the 'save' button in Quantum.

---

