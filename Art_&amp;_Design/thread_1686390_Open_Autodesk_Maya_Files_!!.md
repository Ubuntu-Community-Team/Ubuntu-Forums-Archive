---
title: "Open Autodesk Maya Files !!"
date: 2011-02-12
forum: Art &amp; Design
---

### Post by corefirewire on 2011-02-12
**Hi everyone,**

I am learning Autodesk Maya which is installed in my Windows PC.  Sometimes i need to show some work/problems in my institution but  pen-drives are not allowed there.

I have a netbook with Ubuntu 10.10 32bit installed.

So i was thinking is there **any software which can import the MAYA files (.ma or .mb) **because  installing Maya in my netbook is not a good idea. I don't think Maya  will run with only 1GB of RAM and 1.6Ghz processor. More over i found  that for Linux only 64bit version Maya is available.

I tired Blender but files are not supported.

Please provide some suggestions !!

**Best Regards**

---

### Post by BcRich on 2011-02-12
Hi
you're absolutely right Maya won't run on those specs, but unfortunately your options are quite limited. ma and mb are maya specific file formats meaning that only maya can open them 100% properly. you might get other software that does a fairly decent job but none will be as accurate in representing the data within those files as maya itself.
on the other hand, if you are simply creating 3d models with no animation you can export the files from maya as .obj and import them into blender. which will run on your netbook. .obj will retain mesh data, uv coordinates and therefore also be able to display textures between both applications equally as efficient. If your work in maya does include animation your closest bet for transferring data between applications is the open collada format .dae. I have not used this format but as i understand it's supposed to do animation? but i stand to be corrected on that...
your final option in terms of getting animation into blender from maya would mean, if you are using a skeleton baking out the animation to FK and exporting it as a .bvh file. you'd then have to import that file into blender and reskin the mesh to the skeleton. either way it's probably going to be a bit of work that needs to be done.

---

### Post by corefirewire on 2011-02-12
**Thanks BcRich** ... at present i am doing only modeling. I tried to export files from maya but its not showing any .obj file. Under** File > Export All >** there are **various extensions **like :

Maya ASCII
Maya Binary
mel
move
editMA
editMB
HIKState
HIKCharacter
HIKEffectorSet
HIKPropertySet
FBK export

**I have MAYA 2011, i now 3ds Max has this option but its no where in maya ?**?

---

### Post by BcRich on 2011-02-13
hi
i think that the problem might be that you are trying to export all. try selecting objects individually an exporting them with export selection (you might not have to export them individually, this is just as a suggested precaution). if you don't see the option to export as .obj you'll need to check if the plugin is active in your preferences or download an obj exporter. this is an open format so it should not cost you any money. nonetheless you will definitely be able to export obj from maya as the original developers of maya (wavefront) are also the developers of the obj format, so it will more than likely inherently be a part of maya's core API. good luck :)

---

### Post by corefirewire on 2011-02-13
**Thank you** so much for your replies. This will solve my purpose.

Just out of curiosity i would like to know, how do you know so much about maya? are you into it??

**Warm Regards**

---

### Post by BcRich on 2011-02-13
hi corefirewire
it's my pleasure to offer some assistance where i can. if this does solve your problem please don't forget to click the thread tools arrow at the top of the post and select mark this thread as solved :)
2 b honest I don't really know that much about maya (or i know enough to know that i don't really know very much about it), but i have been producing 3D animation for many years with MAX, Maya and now Blender.
Hope all goes well with your project!

---

