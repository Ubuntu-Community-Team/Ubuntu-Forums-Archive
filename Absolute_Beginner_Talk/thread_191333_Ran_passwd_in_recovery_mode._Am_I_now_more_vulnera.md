---
title: "Ran passwd in recovery mode. Am I now more vulnerable?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by glotz on 2006-06-07
Hi!

I managed to *fcsk up* by changing my keyboard layout and not considering that this would make me unable to login after rebooting, since my password contains characters that are different of those two layouts and that I couldn't reproduce on the latter layout. Great! ](*,)  After panicking for a second I rebooted into recovery mode and used passwd to set a password I could type on the new layout. I can now login again. 

Now, did this running passwd in recovery mode (=as root?) enable the root account or make me more vulnerable somehow? Can it be undone?

Thanks for reading this sad story...

---

### Post by joshrobinson on 2006-06-07
i do it all the time :???:  i like using su in a terminal instead of sudo'ing all of my commands all the time.. as for "less safe" i guess your safe as long as your password isnt something really short and simple

---

### Post by uzi09 on 2006-06-07
you could always re-disable the root account:
```

sudo passwd -l root

```

details:
[https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594](https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594)

---

### Post by joshrobinson on 2006-06-07
next time just boot into recovery mode and run

```
sudo dpkg-reconfigure xserver-xorg 
```

and be sure to select the right keyboard layout

---

### Post by glotz on 2006-06-07
[QUOTE=uzi09]you could always re-disable the root account:
```

sudo passwd -l root

```

details:
[https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594](https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594)[/QUOTE]

Hi uzi09, trying that, I'm getting
sudo: unable to lookup MYPUTERNAME via gethostbyname()
I've change my hostname since, is this a factor in this?

[QUOTE=joshrobinson]next time just boot into recovery mode and run

```
sudo dpkg-reconfigure xserver-xorg 
```

and be sure to select the right keyboard layout[/QUOTE]

I do have now the correct layout, did you miss that in my post or what is this for?

---

### Post by uzi09 on 2006-06-07
hey!

as far as that error, i've seen it come up TONS of times in the threads. I've never had the issue myself, and never bothered to try to figure out what causes it or what its solution is. i'd recommend you do a search for "via gethostbyname()" and see the threads that come up. one of them that *might* have the answer to it is this one:
[http://www.ubuntuforums.org/showthread.php?t=188337&highlight=gethostbyname%28%29](http://www.ubuntuforums.org/showthread.php?t=188337&highlight=gethostbyname%28%29)
but in all honesty - it was a little too long for me to read through completly :S

as far as joshrobinson's advice -- i think he ment that was something you could have tried instead when you were initially stuck. its actually not bad advice at all (i didn't even think about it personally :S), just a lil too late :D or perhaps for future reference

let us know how it goes!

---

### Post by glotz on 2006-06-07
I think that the root account might be there but even if someone figured out the password, it'd be for my old hostname, which is non-existant now. So, no risk I suppose. Unless somebody thinks otherwise, I think I'll do nothing further about this. Thanks for your help!

---

### Post by glotz on 2006-06-08
The saga continues...

Now, having shut down my puter and starting it again, it showed the old hostname again to my surprise! I decided to try disabling the root account and this time it gave better results

c0mm0@OLDNAME:~$ sudo passwd -l root
Password:
Password changed.
c0mm0@OLDNAME:~$

I found my old name in /etc/hostname and changed that, now let's see if it works...

---

### Post by glotz on 2006-06-08
On and on and on...

Just tried to install something and ran sudo apt-get update. I was again greeted by sudo: unable to lookup MYPUTERNAME via gethostbyname(). Looks like I can't do much anything beginning with sudo.

Solved the sudo: unable to lookup MYPUTERNAME via gethostbyname() issue by booting onto the desktop CD and mounting my HDD and editing /etc/hosts which contained the OLDNAME. Now it looks like everything is once again well in the kingdom... :)

Yar-yar Binks would probably say: Crazy shit!!!11

---

