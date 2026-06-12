---
title: "upgraded video card, now Ubuntu won't start"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by rocka on 2007-01-13
Hi all,

a while back I upgraded my video card to a Nvidia Geforce 6800, and now Ubuntu won't start. [The card is ok because Windoze sees it just fine.]

Ubuntu goes through the graphical stuff with the brown background loading its bits and pieces and once it gets to the end it suddenly goes to text on a blue background and says:

"Failed to start the X server (your graphic interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

then there's a YES and a NO button - the YES is in red

But over the top of that box is some more text on a black background:
"Ubuntu 6.06.1 LTS merlin-desktop TTY2
Merlin-desktop login:"

There's no mouse pointer so I can't click on the YES or the NO.

If I type "yes" it asks me for a password...

I don't know what to do next. I don't remember having to log into anything before. Well, I do remember something about a root password but I'm hoping I'm not going to need that because if I do, I'm going to be stumped... 



I did a bit of googling and found this page:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
which starts out by saying the following only works on "breezy"
Is that what I've got?

In any case, I think before I get to try any of that stuff I'll be needing to get around that password problem - can anyone please help?

TIA...
lol

---

### Post by taurus on 2007-01-13
Log in with your username and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```
Then, install nVidia driver for your graphic card once you get X running again.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by rocka on 2007-01-13
this place is simply amazing - such quick replies...
:eek: 
:cool: 

So, now I think this thread is about to take a whole new turn...
What if I can't remember that username and password?
It's been a while now [several months] but I don't recall having to put in any username or password just to start it up and do some web browsing.

Is there a way to get that username and passwork figured out, if I don't have it/can't remember it?

---

### Post by taurus on 2007-01-13
Boot into recovery mode from GRUB menu and at the prompt, have a look at your /etc/passwd to see what it is.  Otherwise, you can look in /home too.

```
cat /etc/passwd
ls -la /home
```
Assuming it is **rocka**, change the password for that user with

```
passwd **rocka**
shutdown -r now
```

---

### Post by rocka on 2007-01-13
thanks for your very fast help - it's fantastic!

But I don't know what you mean by "have a look at your /etc/passwd"
I chose the recovery mode from where I can choose Ubuntu or XP.
It scrolled a few dozed pages of text and then finished with:

root@merlin-desktop:~#

I don't know what to do from there...
I remembered something from the old DOS days - DIR, but that just gives a one word response: Desktop and then root@merlin-desktop:~# again.

I'm guessing there's some way to show the directories and files directly from the text prompt - but I don't know what those commands are...

:confused:

---

### Post by taurus on 2007-01-13
You are currently logged in as root so be careful.  Show me the output of this command then.  Then, I would know your username.  ;) 

```
ls -la /home
```

---

### Post by rocka on 2007-01-13
ok I've got my laptop set up beside the problem machine now so I can type commands and then copy the results [by hand...] over to you.

root@merlin-desktop:~# ls -la /home
total 12
drwxr-xr-x  3 root   root   4096 Jul 2  2006 .
drwxr-xr-x 21 root   root   4096 Aug 5 17:18 ..
drwxr-xr-x 31 merlin merlin 4096 Aug 20 18:08 merlin
root@merlin-desktop:~# _



hope it means something to you...
:???:

---

### Post by taurus on 2007-01-13
Yip.  Your username is merlin.  So, while you are still at the prompt (booting from recovery mode), change the password for merlin with

```
passwd merlin
<type in new password>
<re-type the new password>
```
Now, you can reboot and log in with merlin as username and the new password that you just have created.

---

### Post by rocka on 2007-01-13
ok - we have progress!!!!
:-D 

I'd like to thank you very much for your help - we got past that password thing.
Now I have a graphic display back.

It's installing updates now, downloading package files - I think it will take a while to get through that, there's 93 files to be updated it says...


I'll let it do all that then try updating the driver when it's done.

... I might be back - LOL
:rolleyes:

---

### Post by taurus on 2007-01-13
Yes, just let it run, updating.  And when it's done, reboot to make sure everything is still working and then install the nVidia driver for your graphic card.

---

