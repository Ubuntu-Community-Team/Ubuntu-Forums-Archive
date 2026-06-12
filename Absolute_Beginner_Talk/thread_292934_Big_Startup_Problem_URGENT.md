---
title: "Big Startup Problem: URGENT"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-04
Hi, Im not getting into Kubuntu anymore,
I have installed the nvidia drivers using the following method:

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
 
 $sudo nvidia-xconfig

This worked which I was pleased about, I have rebooted since then with no problem (indicating this is not the problem). However, I was trying to install xlib and installed loads of related packages in trying to get it working. If it helps i recently tried to do a full update on all my packages and that produced an error part way through installing and had to stop, it said it couldnt continue (cant remember exact method). 

Anyway, now it starts up and goes through the normal process with the splash etc..

It gets to the nvidia screen and it comes up for a second then i get a crazy retro style screen for a few seconds and then a black screen with a flashing underline sort of cursor thing in the top left.

Im on my laptop now waiting for the excellent ubuntu community to help me out!

Please help, I need to get my system back!

---

### Post by Ecthelion on 2006-11-04
You can always try to reconfigure your xserver...

do 

Ctrl-Alt-F1

```
sudo dpkg-reconfigure xserver-xorg
```

Although it sounds like it does start up correctly...and then crashes...

If it's not that you could try to do the reconfigure xserver-xorg and choose the generic driver instead of the nvidia driver...

And if it's still not helping...
Then you'll have to wait for someone else to help 'cause I don't know

---

### Post by tommy1987 on 2006-11-04
thanks very much trying it right now..

---

### Post by tommy1987 on 2006-11-04
okay that has not fixed it, I have now realised what the retro looking screen is though, it appears to be the layout of the GUI (second splash) but it is all measurements etc.. Dont think I am supposed to be seeing it.

Oh, I hope I can recover this!

Two other things I noticed on the first splash screen it is saying:

loading hardware drivers.....................fail
mounting local filesystems...................fail

This is sounding scarier and scarier..

---

### Post by blendmaster on 2006-11-04
Try using this code in safe graphics mode:

```
sudo nano /etc/X11/xorg.conf
```

Then locate the drivers section, change where it says "nvidia" to "nv", and then hit ctrl-x, then y. Restart and you should be good.

One method that probably won't work (but has for some problems) is to type:

```
startx
```

Try this after you've done my first suggestion, as it probably won't work anyway (it won't hurt anything to try though)

Hope this helps!

---

### Post by blendmaster on 2006-11-04
By the way, the weird looking splash is a secondary splash that starts up if your first one refuses to start. Don't worry about it, as it really doesn't mean anything bad about the rest of your system (those x-server files anyway).

I know this screen was used in Edgy while it was still "beta", before they added the new one in. I don't know if this is in Dapper though (if you're using Dapper, then I guess it is).

---

### Post by tommy1987 on 2006-11-04
really starting to panic now, anybody else got any other suggestions..?

---

### Post by tommy1987 on 2006-11-04
didnt see you posted a suggestion trying it now.

---

### Post by tommy1987 on 2006-11-04
still no joy with any of the above, I believe it is an xorg problem because of the funny primitive alternate splash that appears. Although it is a worry that it fails to mount local filesystems and locate hardware drivers??!?!

---

### Post by tommy1987 on 2006-11-04
okay, here is what i get now, I now get no splash screen at all, the only fail i am getting is with mounting local filesystem. It goes straight into a text (console) based screen where I have to login, it lets me login and I have total usual access to the system. Where has my KDE gone???? Can I get it back? Im worried and confused!

---

### Post by Ecthelion on 2006-11-04
If you still know which packages you installed you can try to uninstall them...
You could try to reinstall all xserver related packages...
Reinstall Ubuntu-desktop....

Or reinstall your whole pc if you have an separated /home.

Sometimes that's the fastest solution...
But if you don't know which program messed everything up...
Well there's little we can do...

(That's how I feel anyway)

It's up to you...
Reinstalling your gnome / kde desktop might be something you could want to try first...

---

### Post by tommy1987 on 2006-11-04
How easy is it to reinstall KDE?
What would you do. I know what messed it up because I searched around some forums for help installing xlib and someone had replied with a load of packages they said to install because it had worked for someone else. I tried it and this happened!!

I cant seem to find the post now though, it was in this forums I think!

---

### Post by tommy1987 on 2006-11-04
I still think it is salvageable because now Im getting a higher resolution splash screen than before with a different bar its thinner and segemented (dont know how it changed from the default?). However it still goes to command line right afterwards..

---

### Post by tommy1987 on 2006-11-04
reinstalling now, only this time, im not keeping windows, i hope im making the right choice ;-)
Just hope I dont mess it up again..!

---

