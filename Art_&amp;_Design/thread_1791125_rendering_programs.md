---
title: "rendering programs"
date: 2011-06-26
forum: Art &amp; Design
---

### Post by Dungeon_Beast on 2011-06-26
Are there any good ubuntu based rendering programs comparable to the windows programs keyshot, maxwell or vray? I need something that can render Rhino or similar files into graphic images. Bonus points if it does animations, but I really only need single images.

---

### Post by rg4w on 2011-06-26
I'm not a 3D expert so others here may have more informed opinions, but I've been playing with Blender lately and I'm very impressed.  You can find it in the Ubuntu Software Center.  It's also available for Mac and Windows if you need to move work among multiple OSes.

---

### Post by BcRich on 2011-06-27
Hi Dungeon_Beast
[Indigo Renderer]("http://www.indigorenderer.com/home") and [Lux Renderer]("http://www.luxrender.net/en_GB/index") are both physically accurate unbiased renderer's  (like maxwell) that run on Ubuntu. Regarding their native support for Rhino files I'm not entirely certain about that, but they should have some information regarding Rhino support (or lack thereof) indicated on their websites.
They are not as interactive as Maxwell in terms of being able to rotate the viewport while rendering, but there are many image adjustment parameters that can be tweaked while rendering (in as close to realtime as your machine can handle).
Nonetheless this doesn't help you very much if they don't support Rhino files. Is it possible to export the files you are working on to a another format .obj, .3ds, .fbx (and other formats) are supported by Blender. OBJ has the best results for me when transferring single 3D objects between different 3D packages as it also retains UV data. 
this link demonstrates a technique for importing Rhino files into Blender  [http://www.studiorola.com/tutorials/miscellaneous/bringing-rhino-files-into-blender-3d/](http://www.studiorola.com/tutorials/miscellaneous/bringing-rhino-files-into-blender-3d/)
unfortunately you will loose the special surfaces that Rhino uses as your geometry will be converted to polygons (if you weren't already using polys). This will be the case in most situations when transferring Rhino (or any other format) to any program that does not natively create the format you are attempting to import.
It might also be worth noting that Blender has support for several different renderers itself such as [aqsis renderer]("http://www.aqsis.org/") ([gallery]("http://www.flickr.com/groups/aqsis")) which can be setup as a plugin for Blender (I think the plugin might be called mosiac, but I might be mistaken). Aqsis is a Pixar Renderman compliant rendering engine.

---

### Post by a sandwhich on 2011-06-27
Octane is a rather fast physics based renderer that is still in beta. The newest beta is tested and runs on osx, windows, and most major linux distros, ubuntu included. They have a rather good demo if you want to try it out.   [http://www.refractivesoftware.com/](http://www.refractivesoftware.com/)

---

### Post by CreativeReach on 2011-06-28
There is always [yafaray]("http://ubuntuforums.org/www.yafaray.org")! Its stable and works well, Although I still prefer LUX (It can be buggy,but when there done it'll be awesome)

---

### Post by cespinal on 2011-06-28
> **Dungeon_Beast said:**
> Are there any good ubuntu based rendering programs comparable to the windows programs keyshot, maxwell or vray? I need something that can render Rhino or similar files into graphic images. Bonus points if it does animations, but I really only need single images.

Hell yeah! Kerkythea! 

It is the only cross platform professional software I have been able to use in both windows and linux. 

Is totally free, is awesome... 

the only drawback is that I use it in along with sketchup, which only runs on windows....

edit: and it can work with rhino if you export the files as .3ds and .obj

---

### Post by kayosiii on 2011-06-29
off the top of my head
VRay
Mental Ray
PRMan (+ 3Delight & nearly all renderman compliant renderers)
Yafaray
Octane
LuxRender
Blender (+ Cycles)

---

### Post by talebinezhad on 2011-08-27
maxwell runs on linux,mac and windows as well. most world class renderers are also on linux like many rib renderers.you can find some of the most powerful 3d programs on linux too like : maya ,houdini ,blender and ... they come with powerful built in renderers for example houdini's mantra . there are some notable free rendrers : kerkythea ,aqsis ,pixie ,luxrender and so on . if you are talking about rendering i should say you wont need windows anymore .

---

