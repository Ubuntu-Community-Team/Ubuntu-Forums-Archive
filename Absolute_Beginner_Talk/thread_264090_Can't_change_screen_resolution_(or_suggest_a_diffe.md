---
title: "Can't change screen resolution (or suggest a different VNC viewer)"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-09-24
I installed Ubuntu as a LAMP and then installed a GUI

I have just worked out and now working a VNC over SSH, but....

....my resolution is a default at 1280 x 1024

I want to select something smaller so I can view the whole screen instead of having to scroll to get to bits.

Everytime I select a different resolution, ubuntu goes back to the default login screen, and the resolution is still the same. #-o 

I'm guessing that this might have something to do with the onboard graphics that the PC is using...  Now keeping in mind that I'm not going to buy a new graphics card as it is a headless web server, can someone please suggest either

* a solution to this odd problem

* a windows based VNC viewer that scales the window down.

I have tried Real VNC and Tight VNC... but no success (although I'm very new to these programs and may have missed an option somewhere.) 

Help! [-o<

---

### Post by DarkKoopa on 2006-09-25
I've been reading about this a bit more, and I've added

HorizSync 30-86
VertRefresh 48-120

to the monitor section of xorg.conf and still nothing.

When I change it, it dumps my VNC session and I have to reboot (although I'm sure there is a secret restart command to get it going again.)

ARGH!!!!

:-k

---

### Post by DarkKoopa on 2006-09-25
YAY!!!!

I got it to work.

Using the secret restart command 
> 
sudo /etc/init.d/gdm restart

and changing the max sync to 60 I was able to get it shrink resolution, making it viewable under my VNC client.

Now to work out why it's so slow..... :(

---

### Post by dmizer on 2006-09-25
vnc is slow.  there are ways to speed it up, but that's a lot of data to move over your internet connection.

if you're using a lamp server that you intend to open to the web to host a site, turn off vnc.  there are other, better, more secure ways of administering your server.
1) ssh
2) webmin

of those, ssh is probably the best thing you can do.

since you already have a gui installed, all you have to do is connect via ssh as follows:
```
ssh -X yourserver
```
you will get a terminal display.  then you can type in whatever program you wish and it will open on your host computer like you were sitting in front of your server.

---

### Post by DarkKoopa on 2006-09-26
> **dmizer said:**
> 
```
ssh -X yourserver
```

Do you mean exactly like that "yourserver", becasue it didn't work? I even tried the computer name "ubuntu" and all it seems to do is re-login????

I installed and am using FreeNX (which I'm happy to report as a n00b worked straight out of the box so to speak, and when it did need to configure the one thing, I was greeted with the familar Windows type GUI window.  It's the one thing I think Linux really needs to work on to become really mainstream.) :-k 

Seems to be great, and is secure as well.

---

### Post by dmizer on 2006-09-26
i tried 4 times to make this post, but it didn't stick.  hopefully this works out, otherwise i'll have to break out the ubuntu forum mascot.

i made some assumptions in my last post that i shouldn't have.  sorry about that.

forget what i posted before and follow this instead:

you'll need to have two pieces of information before you start this.  since i can't know what they are, you'll just have to replace what i enter with whatever applies to your situation.  these two pieces of information are as follows:
1) "username" <- this will be the user id/account id/user name/ on your remote server you wish to ssh to.
2) "yourserver" <- this will be what the remote server you wish to connect to calls itself.  this can be any number of things, a url, a netbios name, or ip are most common.

so once you have those two pieces of information do the following:
```
ssh -X username@yourserver
```
in the above example, remember to replace username and yourserver with whatever applies to your situation.

this will be far more secure and way faster than vnc.

---

