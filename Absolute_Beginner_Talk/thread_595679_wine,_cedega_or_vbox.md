---
title: "wine, cedega or vbox"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-10-29
i undersatand that cedega is only for games, but this can also be done by wine and vbox??



so whay use vbox and for what, 

why use wine and for what

and why use cedega and fior what??

---

### Post by faraz_k86 on 2007-10-29
ok i just found out that cedega is a paid software.

i dont want to pay for any software thats why i moved to linux

---

### Post by faraz_k86 on 2007-10-29
bump

---

### Post by Hospadar on 2007-10-29
Well, if you can get something to run on wine, you will generally get by far the best performace that way.  As wine is not an emulator (it does not run a copy of windows, it just implements windows system call on *nix) it will use a lot less of your system resources and run stuff a lot faster.

That said, wine oftentimes has some compatibility issues with software as completely re-writing a system api with often little to no documentation is monumental to say the least.  So if you can't run something with wine, then I would try running it in a virtual box.  This will lower your performance a little, but generally yields much better results in terms of compatibility.

So there's no general answer to which you should use, it will generally vary from program to program.  Check the wine appdb for info about specific programs' compatability with wine, and/or see if you can get them to run, and if not, then I would use a virtual box.

---

### Post by rookshop on 2007-10-29
If you are into gaming, then I would suggest Wine. Most of the games I play (Counter-Strike, Warcraft) are on Wine. However, for other software go for VirtualBox. Some software works on Wine too, but installing it takes an effort and even then there are little quirks that are irritating.

---

### Post by saintlostone on 2007-10-30
do you have any suggestions for the easiest newbiest guide to installing and running wine for the first time?

---

### Post by mdpalow on 2007-10-30
go to Synaptic and do a search on Wine; then install it. :)

Doesn't get much easier than that. :)

Have fun...

By the way, you might seriously want to look at / consider VMware, but I don't think it's good for games. GREAT for everything else Windows though.

check out my other post  

[http://ubuntuforums.org/showthread.php?t=596349]("http://ubuntuforums.org/showthread.php?t=596349")

---

### Post by dfreer on 2007-10-30
You can't really use virtualbox/vmware for gaming, I believe due to the virtual driver not supporting 3D apps. Wine is not just for games, it is really designed for any windows software. As mentioned above, it just isn't completed yet, so not every piece of software works. 
When using virtualbox/vmware, since you are actually running windows, any piece of software *should* work, but you'll have to deal with performance issues and a video driver that can't support 3D apps.

---

### Post by Incense on 2007-10-30
My rule is, if it works in wine, then use wine. Otherwise fire up vbox. I don't game though, so that part is not important to me. The only games I do play are run on either dosbox,  GFCE, or just native Linux games.

---

