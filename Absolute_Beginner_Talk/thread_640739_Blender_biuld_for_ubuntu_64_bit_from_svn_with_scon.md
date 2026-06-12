---
title: "Blender biuld for ubuntu 64 bit from svn with scons"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-14
Can anyone help me or point me to a good how to for building blender in ubuntu 64bit
I know it's in the repositories but there is new features that are not available in that version or even the newest on there blender.org thats why I would like to build it from sorce

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-17
anyone? :(

---

### Post by RemmyLee on 2007-12-18
Just came across this thread. What exactly are you having problems with? I've just built it myself without any problems. You just need to make sure you have all the dependencies installed.

You can try to use the build I put together if you like. It's from SVN and has the new Particle System implemented.

[Link]("http://www.badongo.com/file/5648778")

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
all of it mostly the optimization part and the svn part i think 

i would like to build it for 64bit 7.10 ubuntu with the new partical system
and know how to build for the future i will have to read and stuff could you tell me how you found out or how to do it 
thanks
ps i have amd 64bit any diff for intel

---

### Post by RemmyLee on 2007-12-19
[http://www.blender.org/development/building-blender/]("http://www.blender.org/development/building-blender/") should get you going with the dependencies need. Everything is in the repositories. Just make sure to install the -dev files.

In the file CMakeLists.txt, you'll find most of the optional settings.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-20
How can i pick what i would like in there
I just wanna try it with the new partical system
but your build didn't work on my computer
and is your build 64 bit or 32?

---

### Post by RemmyLee on 2007-12-20
I'm not sure how scons chooses the architecture when building, but my system is 64 bit.

Here is a list of the packages you need to build Blender from SVN with scons:

>  python libjpeg62 libjpg62-dev libpng12-0 libpng12-dev zlib1g zlib1g-dev libopenal0a libopenal-dev libsdl1.2debian libsdl1.2-dev libode0debian1 libode0-dev

Once they are all installed, fire up the terminal and type:

> svn checkout [https://svn.blender.org/svnroot/bf-blender/trunk/blender](https://svn.blender.org/svnroot/bf-blender/trunk/blender)
cd trunk/blender
scons

Once finished, you should have a fully working copy in the build directory.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-20
cool thats easier than i thought it would be
do you know if theres a way to pick what new features you build in and what you leave out

---

### Post by RemmyLee on 2007-12-21
Sure is. Once you start building Blender with scons, a file called Config.opts will be generated. Open it up in you text editor and change it to suit your needs. If you don't have any plans on updating the source from SVN or CVS, you can change them directly from within the SConstruct file.

---

