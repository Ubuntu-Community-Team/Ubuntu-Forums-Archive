---
title: "Remote terminal/Desktop"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by laika$ on 2007-08-09
I've searched about and read alot of posts, but still unable to determine how to do what I would like to do, though I'm sure it's out there, and I just don't know what to look for.

For those that know windows, i'd like the equivalent of "terminal Services" - where I have a "window" into a session that's actually running on another machine.  Sort of the gui equivalent of ssh.

I'd like my Ubuntu install to be the server and my windows machine the client.  I'd like the login to NOT be a view into the currently-logged in user on the Ubuntu machine, but rather a different session.  Similar to Terminal Services, I'd like to be able to disconnect, while leaving the remote session running, and re-login to it later.

I'd also like the currently-logged in user to see nothing when I do that.

BTW, I'd ALSO like to be able to log in and see what the currently-logged in user's doing (a la "Log Me In" for those familiar with that), but that's secondary.

Thanks.

---

### Post by asmoore82 on 2007-08-09
you can forward X11 over ssh, the Ubuntu Server needs the openSSH package and service enabled.

the Windoze client needs PuTTY to handle the SSH stuff and Xming to handle X11 stuff

are these machines sitting beside eachother?

all that "be able to see"/"not be able to see" stuff sounds a little convoluted ...
**w**,**who**,**ps** and **top** will reveal the truth.

---

### Post by petit.padavoine on 2007-08-09
There are two ways.
ssh -X <user>@<computer> which will give you a terminal like ssh does but which will let you run GUI apps installed on the other computer.
VNC Viewer will open a window where you see the other computer's screen and can use it as if you were sitting in front of it.

---

### Post by laika$ on 2007-08-09
> **asmoore82 said:**
> 
all that "be able to see"/"not be able to see" stuff sounds a little convoluted ...
**w**,**who**,**ps** and **top** will reveal the truth.

when I say "not be able to see" I don't mean completely invisible.  But if my son is surfing on his computer, I'd love to be able to log in to do updates, etc, without disturbing him.  I know it can all probably get done on the command line, but even Unix has adopted the gui for lots of good reasons.

"forward X11" - how?  I've got an ssh server working on the Ubuntu machine already.

---

### Post by petit.padavoine on 2007-08-09
Like the way I just posted:
ssh -X

---

### Post by bodhi.zazen on 2007-08-09
ssh -X is very nice, here are some alternates.

Also see the link on securing ssh !

[http://ubuntuforums.org/showthread.php?t=256102](http://ubuntuforums.org/showthread.php?t=256102)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

And, last FreeNx is popular as well ...  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by laika$ on 2007-08-09
Thanks for all the quick responses, but there is one bit of added complexity - I'd like the remote machine (the client) to be a windows box.  From what I'm reading, ssh -x and freeNX are both unix solutions.  Is there an equivalent for windows?

I've looked at the vnc documentation, but that seems to only allow you to see the currently-logged-in user's session/desktop.

Thanks.

---

### Post by laika$ on 2007-08-09
BTW, it seems that freeNX has the same limitation that vnc appears to - you can only see the currently-logged-in user's desktop.

thanks.

---

### Post by bodhi.zazen on 2007-08-09
I do not know about the windows side of things, but this lnik I gave you :

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

generates a separate session (NOT vnc into a users desktop) ;)

---

### Post by laika$ on 2007-08-09
Thanks I hadn't read that because I didn't care about tunneling (internal network access only).  I have one more question:

is it the ":1" in the "vncserver :1" command that causes vnc to present a new desktop instead of using ":0" to see the "current" desktop?

---

### Post by MenZa on 2007-08-09
The way you forward X11 onto a Windows box is by installing an X server on your Windows box (I think there's one called Xfree86). Then simply enable it in PuTTY.

---

### Post by bodhi.zazen on 2007-08-09
> **MenZa said:**
> The way you forward X11 onto a Windows box is by installing an X server on your Windows box (I think there's one called Xfree86). Then simply enable it in PuTTY.

I have used cygwin (with ssh & Putty) : [http://www.cygwin.com/](http://www.cygwin.com/)

But that is an advantage of vnc, it includes X


> **laika$ said:**
> Thanks I hadn't read that because I didn't care about tunneling (internal network access only).  I have one more question:

is it the ":1" in the "vncserver :1" command that causes vnc to present a new desktop instead of using ":0" to see the "current" desktop?

Yes :twisted:

---

### Post by neuralzen on 2007-08-13
Well, I've installed freenx and everything, and I can login just fine into the normal gnome session, but how do I log into a XGL session running COMPIZ-FUSION? Any help on this would be great! If VNC can do it, one would think that freenx can. Thanks for your thoughts!

  -NZ

---

