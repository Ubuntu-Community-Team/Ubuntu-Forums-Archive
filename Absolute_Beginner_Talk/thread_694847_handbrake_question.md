---
title: "handbrake question"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2008-02-12
I downloaded and ran ./jam,,,it ran through the install and at the end came back to the terminal cursor. Where do i find the program as it doesnt seem to install any icon thanks

---

### Post by LowSky on 2008-02-12
type ```
 jam --help
```

it should give you a list of commands

most likely type ```
jam
``` should start it up

---

### Post by allsys3 on 2008-02-12
im sorry i wasnt very clear. i downloaded program called handbrake for ripping dvd's. in the program folder i was told to run ./jam which i believe is like running ./make to load the program. it seemed to go through the install and then returned to the cursor again. yet i find no sign of the program on my system. :(

---

### Post by jmap82 on 2008-02-20
I'm very much open to correction if I'm wrong... I'm an extremely new user to Linux and Ubuntu, but I think the problem might not be the "install" or the "program" its what you are looking for.  On Linux I believe that Handbrake is only available as a Command Line Interface... I gather this from the download page.( I love Handbrake, but I've only ever used it on my Windows machine in a GUI).  So while you are looking for a "program" all you really need to do is just start typing what you want Handbrake to do into the Terminal because all the "install" did was add some new DLLs and definitions to the Terminal tool box, if you know what I mean.

Long story short, it seems you are looking for a GUI when you don't get one of those in Linux for this particular application.

Once again, I could be wrong, and if I am please correct me, as I am just as anxious to start using Handbrake on my Ubuntu machine as anyone else reading this post.

Peace.

PS- The latest version of Handbrake just came out!

---

### Post by wednesday allfather on 2008-02-29
Hey,

I'm new to the forum, but I think I have an answer for you.  Check out this link.

[http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322&release_id=553070](http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322&release_id=553070)

this should provide what you need for GTK GUI for handbrake.  If I understand correctly, that is just what you are needing.  

Post again if you need help installing it.

---

### Post by badmedic on 2008-02-29
That is correct. On Linux, Handbrake is only available as a CLI (Command Line Interface). If you dont want to learn how to run it in a terminal... and I dont blame you if you don't :)
... you will need RippedWire (HandbrakeGTK) from the link in the post above. It is a user interface similar to the Handbrake GUI on the Mac and Windows.

---

### Post by jmap82 on 2008-03-03
Thank you allfather! 

That is a huge help.  I had started to try to use the CLI version, but it was becoming a real hassle going back and forth from Handbrake's wiki trying to figure out if I had entered everything correctly.  The GUI seems to be working perfectly!  Thanks again for the link!

Note for other newbs like me:... you only need to download/open the .deb file :).

---

