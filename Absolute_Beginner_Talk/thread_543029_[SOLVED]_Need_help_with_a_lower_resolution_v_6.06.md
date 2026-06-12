---
title: "[SOLVED] Need help with a lower resolution v 6.06"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-04
Hi all, im using a visiontek X1550 GPU, and all of my computer components are brand new, however, i do not have money for a new monitor, so im using one from 1995, THIS raises problems, ive just installed and now i cant get my resolution to go any lower then  1200 by 700, or whatever it is, i need it to be at 800 or lower... i go to "change resolution" click on the 800 one, then click OK, it freazes, sizes up to what i asked, then sizes down, and brings me to sign in, i sign in, and its the same, any help please?

---

### Post by pizzutz on 2007-09-04
I would recomend booting up your computer, leaving it at the login screen, and hit ctrl-alt-F1.  this will switch you into a text login prompt. Login as normal, and then type 
```

sudo dpkg-reconfigure xserver-xorg
```

This will walk you through setting up your graphics drivers for X.  it will allow you to pick resolutions availible, and may even be able to detect your moniter.  It should help you reconfigure your settings to be appropiate to your monitor.  There is a lot of stuff in there, and you can pick the defaults for most of it, so don't get scared. when you are done hit ctrl-alt-f7 to get back to your login screen and then ctrl-alt-backspace to activate the new settings.


cheers

---

### Post by xxhaloownerxx on 2007-09-04
having a problem, i did what you said, only problem is, it wont let me insert my password, im typing and im getting nothing on the screen, however i am able to enter in my login name, just not the pass, ill re-boot and change it so there is no pass.

---

### Post by splintercellguy on 2007-09-04
On *nix OSes, typing a password doesn't show anything. It's reading the input, but doesn't show for security.

---

### Post by bruce2000 on 2007-09-04
That is normal - when you type a password into a terminal nothing is shown on screen as a security measure. Rest assured your password will be accepted.

---

### Post by xxhaloownerxx on 2007-09-04
alright ill try it, restarting.


Im not sure if it worked, it gave me my last login, and told me that it comes with no warrenty, ill try the code now.

EDIT: worked i got a blue and gray screen. 

Edit 2: alright im stuck, i got to the configuring xserver, and i clicked auto detect, but im not sure what to do now, its asking for a desired X server driver...

EDIT 3: if i think im right, i have to select the chipset maker? then it would be ATI..

EDIT 4: *smack* dont know what i did now, but it appears i completely messed it up....

---

### Post by xxhaloownerxx on 2007-09-04
i have no idea what to do now.... but i got an error, about it not being set up correctly...., and now all i get is a black screen with a underscore..... can i restart my computer and do defaults?

---

### Post by xxhaloownerxx on 2007-09-04
guys please, im on the verge of tears right now, i dont know what to do, can i restart my computer, please, will my computer be alright?

---

### Post by xxhaloownerxx on 2007-09-04
guys PLEASE, if ive messed up my computer, can i delete the disk somehow? perhaps re-install ubuntu?

---

### Post by xxhaloownerxx on 2007-09-04
nevermind, i just restarted it, and so far im having no problems, but after that scare i think ill stick with my 1200 by 724 res. thanks for trying to help me though, im a total idiot when it comes with computers, just in case you didnt notice with my panicing. marked as sloved.

---

