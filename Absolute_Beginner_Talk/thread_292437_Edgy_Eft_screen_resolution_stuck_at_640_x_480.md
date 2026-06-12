---
title: "Edgy Eft screen resolution stuck at 640 x 480"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2006-11-03
I have a Windows / Edgy Eft box. When I boot into Ubuntu the screen resolution is set at 640 x 480, with no other options displayed to change it to in the screen resolution dialog.

This happened sometimes in 6.06. I'd restart Ubuntu, and the correct resolution would be back. But that's not working now.

Ideas? Is there a text file I can tweak to fix it?

---

### Post by cantormath on 2006-11-03
> **bobmorris said:**
> I have a Windows / Edgy Eft box. When I boot into Ubuntu the screen resolution is set at 640 x 480, with no other options displayed to change it to in the screen resolution dialog.

This happened sometimes in 6.06. I'd restart Ubuntu, and the correct resolution would be back. But that's not working now.

Ideas? Is there a text file I can tweak to fix it?

I would start with dapper, not edgy......but whatever.

What kind of video card do you have?
is this a laptop? what kind?
have you tried automatix2?

---

### Post by bobmorris on 2006-11-03
It's an old P3 desktop, has been working fine with Ubuntu for a couple of months. Standard vanilla video card. 

It's also taking a couple of minutes to boot into both Windows and Ubuntu, so maybe something else is going wrong. Hmmm.

What does automatix2 do?

---

### Post by solasaurus on 2006-11-03
What is the resolution that is possible for your screen and video card? What resolution would you like?

I ask the first question because with my Dell Inspiron 6400 I was stuck with 1024x800 even though it was supposed to do 1280x800. I searched these forums and found out I needed to install a package called 915resolution. I did this and everything worked out fine after restarting the Xserver (eg: by logging out and logging in again). This will work for some people with this kind of hardware. There may be an issue related to your specific hardware that requires a fix.

But if you've got fairly generic hardware and you don't mind getting your hands dirty, the file you want to edit is /etc/X11/xorg.conf. The sections under "Monitor" and "Screen" (which actually refers to video card config) are the ones you need to edit.

---

### Post by baysiqq on 2006-11-03
This didnt work for me. It says that i should be able to pick some resolutions other than 800x600, but it wont actually let me.

---

### Post by bobmorris on 2006-11-03
It's a new Dell 17" monitor working at 1280 x 1024 in Windows just fine.

Do I need to edit the conf file with a special editor? I think I do, what's the syntax? Thx.

---

### Post by bobmorris on 2006-11-03
I found this page

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

And did Th script at the top. It asked questions that I didn't know the answers too so I exited w/out finishing, it said do ctrl-alt-backspace to restart x ... and it worked.

The screen resolution is now back to 1280 x 1024. 

If it happens again, I'll try restarting again.

Go figure!

---

