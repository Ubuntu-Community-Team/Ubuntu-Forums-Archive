---
title: "Internet Dj console probelm."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by FlashBastardDX on 2008-03-19
When I go to open up IDJC from my applications menu, it shows the "Starting internet dj console" on my task bar, but then it goes away, and the program doesnt load. Any ideas what I could been doing wrong? Also, I got it from the Add/remove, if that matters.

---

### Post by phiphedog on 2008-03-19
Try and start it from the command line. It should tell you where it fails.

---

### Post by FlashBastardDX on 2008-03-19
how do I do that? (I know, I'm laughably noobish when it comes to using Linux)

---

### Post by phiphedog on 2008-03-19
I'm not sure of the command.

It's probably ```
idjc
```

You can right click-->properties the icon you use to start it and see what command it is running.

If you can't find the command the ways mentioned then play around with this

As the name of the application is internet DJ console you can try typing in 

i

To the terminal and hitting tab twice, this will list all the commands that start with i.

---

### Post by FlashBastardDX on 2008-03-19
andrew@randy-linux2:~$ idjc
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 2172, in <module>
    run_instance = MainWindow(sys.argv[1:])
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 1308, in __init__
    os.symlink(home + "/.idjc/", home + "/.idjc/profiles/default")
OSError: [Errno 17] File exists

---

### Post by phiphedog on 2008-03-19
Sorry mate, these errors are way above my level of expertise. Perhaps the IDJC homepage has some support forums or try searching for the error it is giving you.

perhaps you could rename the /home/andrew/.idjc/profiles/default file and try restarting it, or renaming the entire /home/andrew/.idjc folder and letting it be recreated when you atrt the application. Not sure if either of these suggestions will work. I'm just clutching at straws now.

Can anyone else help out here?

---

### Post by FlashBastardDX on 2008-03-22
I don't have a home/andrew/idjc folder...

---

### Post by phiphedog on 2008-03-22
Sorry, I assumed from your post above that your username you sign in with is andrew.

The folder will be /home/'username/.idjc

---

### Post by FlashBastardDX on 2008-03-23
No, that is the username, I just don't have said file...

---

### Post by Steveway on 2008-03-23
How did you install it?
Do you allready have Jack running?

---

### Post by FlashBastardDX on 2008-03-24
I got it from the add/remove thing, and I'm sure sure about Jack...All I know is that it worked before, and out of the blue it doesn't anymore...

---

### Post by Steveway on 2008-03-24
I'm not too sure about the error but you should update your version of IDJC.
Apperantly Gutsy only has 0.6.9 and Hardy has 0.7.0 that is pretty old.
I made a .deb of the new 0.7.3 version earlier yesterday, I'm gonna post it tomorrow.

---

### Post by StephenF on 2008-03-25
> **Steveway said:**
> I'm not too sure about the error but you should update your version of IDJC.
Apperantly Gutsy only has 0.6.9 and Hardy has 0.7.0 that is pretty old.
I made a .deb of the new 0.7.3 version earlier yesterday, I'm gonna post it tomorrow.
Have you considered uploading this package or something similar to Debian? It appears that nobody at Debian is taking an interest in IDJC with the result being that Ubuntu is falling behind. All 0.7 versions of IDJC prior to 0.7.3 have some rather nasty bugs and should not be used.

---

### Post by Steveway on 2008-03-25
> **StephenF said:**
> Have you considered uploading this package or something similar to Debian? It appears that nobody at Debian is taking an interest in IDJC with the result being that Ubuntu is falling behind. All 0.7 versions of IDJC prior to 0.7.3 have some rather nasty bugs and should not be used.

I make my .deb files only with checkinstall. Making .deb files for inclusion in a repository is a slightly different job.
It's wise to install IDJC from the repos first if you want to use my .deb since I don't think that my .deb will fetch the required dependencies.
Well, what you maybe want to know about the .deb...:
It's made with checkinstall.
I didn't add anything, but beware it's free software and use at your own risk.
You **won't** be able to use your .wma files with it, that's a decision on my side, personal and ethical.
I tested it on my machine (except the connection to a server wich I did not test yet.) and it works everything.

---

### Post by FlashBastardDX on 2008-03-26
Well, I got it working, however, I can't get my songs to show up in the playlist thing. Also, when I try and use the mic, it just echos a loud, annoying sound.

---

### Post by FlashBastardDX on 2008-04-05
Sorry for the bump but, to be clear on the problem now, I have IDJC hooking up to my server, and jack running. The problem now is that I can't add songs to the playlist. Also, whenever I try to activate my mic, I get this loud screeching sound. I'm not sure if that sound play over the station, but I know it's annoying.

---

