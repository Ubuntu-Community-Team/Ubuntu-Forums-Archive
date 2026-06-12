---
title: "No Screen after system boot..."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Difranco1911 on 2008-02-17
Okay here is the deal.

I went away for the weekend, my shut my computer down and everything was good to go.  I get back this evening and start my computer and it just goes to a black screen with the monitor in sleep mode.  (amber LED)

So I boot to 'recovery mode' and I tried running / reconfig on the xserver which didn't seem to help anything.  What do I do now?

Thanks in Advance...

---

### Post by spiderbatdad on 2008-02-17
try hitting the esc key a couple of times every 30 secs. or so and give it 4-5 minutes to see if it eventually boots. If this works, I have found editting the usplash.conf file to 1024x768 fixes the problem. Note this is only for usplash...doesn't change system resolution.

---

### Post by sabatron on 2008-02-17
This is a bit wacky...but did you try shutting your monitor off and turning it back on.  because when my x server screwed up a while back it gave me a blue screen and had an error like "could not configure x server" or something like that.  But since you dont have an error message it could be your monitor maybe?

---

### Post by Difranco1911 on 2008-02-17
I have tried this without any change in 

It's as if the system is idle, but doesn't seem to be locked up.  I hit the capslock, numlock, etc. and the kybrd lights go on and off.   However there is zero disk activity.

If I hold down the esc key, I get the system beep sound of the keyboard buffer being full.

Also another thing to note is that if this were strictly a video issue, if I hit the power button shouldn't the system shutdown safely?  This does not happen currently.  I have to hard power off by hold the power button in for 15 seconds.

---

### Post by sabatron on 2008-02-17
Take a look at [http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39288346,00.htm]("http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39288346,00.htm")

---

### Post by Difranco1911 on 2008-02-17
that didn't seem to help much...  I couldn't find the inittab file that the article spoke of.

---

### Post by Difranco1911 on 2008-02-17
what else can I do to recover?

---

### Post by Difranco1911 on 2008-02-17
Okay...  well I am lost at this point. 

I can boot from the CD and browse the filesystem fine.  So I am trying to back up my Home directory to my external drive but I can't copy anything because of lack of permissions.  How do I take ownership and set the permissions so that I can read everything and copy to the external drive?

---

### Post by Difranco1911 on 2008-02-18
Okay new wierdness....

I am able to logon and get to the desktop just fine,  If I hit Ctrl-Alt-Del....

anyone seen this behavior before?

---

### Post by 2dere on 2008-02-21
I have been in exactly the same boat as Difranco1911 minus his last comment.

with instructions from another thread I ran 
```
sudo dpkg-reconfigure --p high xserver-xorg
```
And found that I managed to boot normally and as far as I'm aware fix my problem. I'll quote thread when I find it. ( I saved it on my windows bookmarks >.< )

---

