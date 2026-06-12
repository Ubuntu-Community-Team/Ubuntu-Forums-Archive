---
title: "Terragen equivalent"
date: 2006-11-17
forum: Art &amp; Design
---

### Post by thierryl on 2006-11-17
Hi, I have been a linux user since Slackware 1.1 but just started using Ubuntu several months ago.  I am actually quite impressed and have been recommending it all over the place.  So far I have been able to replace just about all my WinApps but I am still left finagling Wine into running Terragen for me.

Does anyone know of a Linux equivalent for Terragen? I would prefer Open Source of course but it would be nice to finally put Wine and my Windows partitions to bed!

Thanks!

TSL

---

### Post by spyke01 on 2006-11-17
No unfortunately not, i use Dundjinni but havent tried it in cedega or wine yet

---

### Post by thierryl on 2006-11-17
Actually I am not sure if that app would fill the bill... this is the sort of artwork I am producing with Terragen at this time:

[Noon At Midnight]("http://www.deviantart.com/deviation/43138792/?qo=4&q=by%3Athierryl&qh=sort%3Atime+-in%3Ascraps")

Other examples are at my website: [digital.twilight.bruce.county]("http://mark.indigoblues.ca")

:)

---

### Post by smartalecks on 2006-11-17
Hi, 

I have looked before, and I can say that there is no equivalent to Terragen in Linux. That being said, I have not tried it under Wine and would not suggest doing so because of the extra time it would take to render. I recommend just using it on another computer if you really need it.

---

### Post by uuwatti on 2006-11-18
there are few, but not as good or anywhere near it. heres one: [http://planetgenesis.sourceforge.net/]("http://planetgenesis.sourceforge.net/")

---

### Post by smartalecks on 2006-11-21
Hey-

browsing around quickly and I found this program:

[http://www.stellarium.org](http://www.stellarium.org)

It doesn't render terrains like terragen but it does render skies and some terrain. Its pretty good.

Should be in the repos.

---

### Post by Dml on 2006-11-22
I don't think there exist any equivalent... CG software is rather rare, special thing. Actually i do have sort of ["terragen equivalent"]("http://dmytry.pandromeda.com/voxelworld/images.html") developed by myself but it is not exactly enduser usable, and to tell truth i don't maintain it anymore.

You can maybe use pov-ray to render terrain scenes under linux tho.

---

### Post by smartalecks on 2006-11-22
> **Dml said:**
> I don't think there exist any equivalent... CG software is rather rare, special thing. Actually i do have sort of ["terragen equivalent"]("http://dmytry.pandromeda.com/voxelworld/images.html") developed by myself but it is not exactly enduser usable, and to tell truth i don't maintain it anymore.

You can maybe use pov-ray to render terrain scenes under linux tho.

Thats very cool! But whats with the executable :/ ?
What is it written in?
Do you have any plans in continuing it?

---

### Post by Dml on 2006-11-23
It's written in Pascal, a while ago (somewhere between 2002 and 2004), compiles with Free Pascal Compiler (i.e. it runs on linux too). The sources is somewhat horrible. It started in days when use of integer only math still seemed like a good idea. 
The last development i did was in 2005 summer, quickly fixing up a few animation issues for some minor commercial use (it render images about 100 times faster than terragen) but it wasn't really used unfortunately. 
I *can* release it as OSS, but will anyone maintain it or use it? Unfortunately i don't have time to, or time to look for maintaners.

Currently i'm working on entirely different rendering engine... You can check the MojoWorld section on my website, especially Volumetrics subsection and Erosion Fractal. Mathart section is also good.

---

### Post by efflux on 2006-12-13
Hi Dmytry.

You'll know me from the Mojoworld forums.

If only there was any decent landscape generator that ran on Linux. I assume Mojoworld still doesn't run under Wine.

Planetside who make Terragen have said in answer to the FAQ:

Will TG2 be available for Linux?

"We will almost certainly have a command line render engine for Linux. The decision about a full GUI application is yet to be made."

This is one good step at least. It means you could use a Mac and wouldn't need Windows for huge multi machine renders.

Windows XP has just locked me out of one PC. I can't activate again so I'm locked out of doing big Mojoworld renders now since it can only use one core on my Mac and I need the Mac for other stuff. Of course I can stick a pirated XP Pro on there but it's the principle. MS forcing me to criminality when I simply made one to many hardware changes to the same system. Mojoworld is the only program keeping me on Windows.

---

### Post by DarkN00b on 2006-12-13
I have tried Terragen in Wine, but I get the dreaded "Error 355-unable to access the system registry" error. I have searched for Linux programs that are capable of the great quality pictures produced by Terragen, but have so far been unsuccessful.

---

### Post by Steve S. on 2006-12-13
Yeah, terragen and some of the other graphics stuff is only thing that keeps me dual booting.

Be glad to know when they come up with a good terragen alternative, or when terragen gets a good linux gui.

---

### Post by riny on 2007-01-17
the Old version of Terragen, v0.9.43, can be installed in Wine. You have to download four extra DLL to run it:
msvcrt.dll
msvcrt20.dll
msvcrt40.dll
msvcrtd.dll

Those can be put in the system32 folder. 

Use winecfg to set Wine to use those native. Then it works fine. :) 

I run it this way for some time now. I am still looking for a way to run Terragen 2 Technology Preview.

---

### Post by Eggbertx on 2009-03-30
can't you just get the source? or is it not open source?

---

### Post by Dml on 2009-06-06
Yes, its open source now, albeit unmaintained.
Get source from there and follow build instructions. You will need Free Pascal Compiler (it is written in Pascal)

[http://dmytry.pandromeda.com/voxelworld/downloads.html](http://dmytry.pandromeda.com/voxelworld/downloads.html)

---

### Post by Talorgan on 2009-07-18
> **spyke01 said:**
> i use Dundjinni

Can anyone recommend a program capable of producing detailed top down maps. I don't need the full 3D.

Dunjinni was too crude. Sudden Strike III's map editor didn't give enough detail, Blitzkrieg II's gave enough detail but the objects weren't maleable and "fish-eye" (lack of an orthographic view, if that's the right word) was a problem on bigger maps.

Google SketchUp Pro would probably fit the bill if I had a spare $500!

I've tried drawing freehand with GIMP and that was less than satisfactory.

I don't think you can add buildings to Terragen.

---

### Post by Talorgan on 2009-07-29
Might the answer to this be "Ogre" or "FreeWorld3D"?

---

### Post by arkor on 2009-11-08
> **riny said:**
> the Old version of Terragen, v0.9.43, can be installed in Wine. You have to download four extra DLL to run it:
msvcrt.dll
msvcrt20.dll
msvcrt40.dll
msvcrtd.dll)

Those can be put in the system32 folder. 

Use winecfg to set Wine to use those native. Then it works fine. :) 

I run it this way for some time now. I am still looking for a way to run Terragen 2 Technology Preview.
  
Hi. I have Terragen v0.9.43 and am running Linux Mint. I had msvct.dll already so I downloaded the other 3 files, and have used the Wine config to set all 4 files initially to native/then builtin (the default). However, was unsuccessful in running Terragen as it flickers for a second and then nothing. So I then tried setting the 4 files to Native Windows, but then get error message "Runtime error '53': File not found Terragen".  I see that you are listed as using Hardy so perhaps maybe not able to run in Mint? I also have a netbook running the Ubuntu netbook remix. Have not tried it on there because I have no plans on running Terragen on it. Has anyone else gotten it to run? and if so, how? and on what distro? I'd hate to have to go back in time and use the Hardy Heron.

---

### Post by texaswriter on 2010-07-12
In case anybody is still watching this thread. 

[http://www.codeweavers.com/compatibility/browse/name/?app_id=7704;forum=1;msg=84561](http://www.codeweavers.com/compatibility/browse/name/?app_id=7704;forum=1;msg=84561)

Terragen 2 can be got to work by following the directions via the above link. I have used it to render very complex scenes without any problems whatsoever.

---

### Post by Talorgan on 2010-07-19
> **texaswriter said:**
> In case anybody is still watching this thread.

Thanks

---

### Post by texaswriter on 2010-07-21
> **Talorgan said:**
> Thanks

Yeah, definitely, Codeweavers Crossover Games / Linux is a great product. I would recommend trying it out and supporting it if it helps you out. 

Good luck with that!!! and post screenshots... Also, post on the forum in the above link with what version of Terragen 2 you are using, paid, free, etc... and your computer specs...

---

