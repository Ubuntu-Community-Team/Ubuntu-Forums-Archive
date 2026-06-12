---
title: "Two problems..."
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-05-05
Alright, so here's the rundown.

I just updated my kernel on Dapper to the newest version.  I went to go play a CD and the drive wouldn't mount!  I don't quite know what's wrong there...

and!

I have updated the xorg.conf resolution sizes but System->Preferences->Screen Resolution still only shows 3.

Any suggestions?

---

### Post by ComplexNumber on 2006-05-05
> I went to go play a CD and the drive wouldn't mount! when you say it won't mount, what do you mean exactly?


>  I have updated the xorg.conf resolution sizes but System->Preferences->Screen Resolution still only shows 3.
there should be a menu option in your main menu called Display. change the resolution there.

---

### Post by mcmillan on 2006-05-05
I'm assuming you mean you're trying to play an audio cd. You don't actually mount audio cds, they just get played by whatever media player you're using. If it's not playing anyway then there's some other issue we need to figure out.

---

### Post by masooga on 2006-05-05
The computer doesn't recognize the CD I put in /media/cdrom0 is empty.

---

### Post by Sef on 2006-05-05
> The computer doesn't recognize the CD I put in /media/cdrom0 is empty.

Have you tried seeing if other CDs work?  You may have a bad CD.

---

### Post by masooga on 2006-05-05
Yeah, I've gone through about 4 different CDs.  The one I am on now works in one of my other computers.

---

### Post by confused57 on 2006-05-05
Do you still have these problems booting into the old kernel?

---

### Post by masooga on 2006-05-05
I don't know how to do that and I had to upgrade because my sound wouldn't work in the old kernel and that was the suggestion I got.  Sound works now.

---

### Post by Sef on 2006-05-05
> Sound works now.

It's so nice to have it working. :)

---

### Post by confused57 on 2006-05-05
When your system is booting, there is an option to press "Esc" to enter Grub, usually you only have 3 seconds to do this(there is a way to edit your menu.lst to increase the time, but that's another topic).

The highlighted kernel should be the latest and is what Dapper boots into.   There will be other options listed below this, press "arrow down" then enter, hopefully this will boot you into the old kernel.

You'll also see other options, such as "rescue mode", "memtest", which are good things to be aware if you have problems.

Keep us updated, someone will probably know the answer.  May be a bug in the new kernel related to your hardware or just some simple configurations?

---

### Post by masooga on 2006-05-06
It works when I switch to a different kernel.

---

### Post by confused57 on 2006-05-07
Hopefully, Dapper updates will eventually fix the "bugs" you've encountered with the new kernel.
   Do you plan on routinely booting into the new or old kernel?  You can change the default in your grub menu.lst to do this until there is a fix to the problem.

---

### Post by masooga on 2006-05-07
I'd like to keep using the newer kernel but I guess I'll have to run back to the old one.

How should I describe the problem when I'm reporting the bug?

---

