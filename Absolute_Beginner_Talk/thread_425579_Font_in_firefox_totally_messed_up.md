---
title: "Font in firefox totally messed up"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-27
A few days ago, I had a problem of corrupted user profile and the font in Firefox started to mess up shortly after. 
Note: This issue doesn't occur in OpenOffice or any other program. 

Anyways, when I view a post in Ubuntu forums and certain other forums, "k" and numerals look kinda funny.

I've tried creating a new profile, switching fonts used in Firefox and even reinstalling Firefox but to no avail. I've also looked up several threads about fonts in Firefox but I'm a little stuck. 

Also, these are my default Font settings in Firefox.

Edit---->Preferences---->Content
Default font: sans-serif

Edit---->Preferences---->Content(Advanced font settings)
Proportional: Sans-serif
Serif: Bitstream Vera Serif(I changed this from the original font settings to try and remedy the problem.)
Sans-serif: sans-serif
Monospace: monospace

Anyways, here's a screenshot of my issue.

[[IMG]http://img257.imageshack.us/img257/3706/fontfirefox1ct1.th.png[/IMG]](http://img257.imageshack.us/my.php?image=fontfirefox1ct1.png)

Thank you for reading! :)

Edit: It's kinda funny, though. I think I got this problem in Windows too but I don't remember what I did to fix it.

---

### Post by LuisGMarine on 2007-04-27
I think those are how my fonts looked when I first installed Ubuntu.  I was just wondering, do you happen to be using an LCD or a CRT monitor?  Either way head over to System > Preferences > Font .  There is an option for Font Rendering.  By default mine was set to ' Best shapes ' , but once I changed it to ' Subpixel smoothing ( LCD's ) ' it completely made everything much better.  Looks exactly like smooth fonts in Windows, which is what I think you were referring to.  Anyhow I hope this works for you!

Good Luck

-LuisGMarine

---

### Post by Lucifiel on 2007-04-27
> **LuisGMarine said:**
> I think those are how my fonts looked when I first installed Ubuntu.  I was just wondering, do you happen to be using an LCD or a CRT monitor?  Either way head over to System > Preferences > Font .  There is an option for Font Rendering.  By default mine was set to ' Best shapes ' , but once I changed it to ' Subpixel smoothing ( LCD's ) ' it completely made everything much better.  Looks exactly like smooth fonts in Windows, which is what I think you were referring to.  Anyhow I hope this works for you!

Good Luck

-LuisGMarine

I have a CRT monitor and actually, I tried that already. However, it didn't work at all, not even after I restarted the browser. Nor did restarting Ubuntu help. 

Seems like the font used for reading text is a bit broken or something. Man, I really hope I can find a solution for this as reformatting seems a pretty drastic measure and I can't read the text properly.

---

### Post by Lucifiel on 2007-04-28
So, does anybody know what font the Ubuntu forum uses? I'd like to look further into this issue.

---

### Post by Lucifiel on 2007-04-30
Bump

---

### Post by Lucifiel on 2007-04-30
All right, I actually upgraded my font packages a few weeks ago using the instructions from this thread. So, I downgraded them to the 0ubuntu1 versions and the problem still remains. So, I upgraded them again. 

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

Now, I thought of replacing my Ubuntu default fonts but I can't even find the font folder in the Feisty cd-rom. Gah... -_-;; I'm not sure what to do anymore.

---

### Post by LuisGMarine on 2007-05-02
After messing around with some of those mstrufontscore w/e package, I have to add that my firefox is also displaying very very bad rendered font.  I see this is opera too :(

I'm on your boat now, I have tried soo many thing out there but it seems to be just firefox.  Everything else on the gnome desktop is completely fine, as far as text goes ;)

But then you get here to Firefox and everything just takes a big huge dump :(, I'll keep you posted if I find a fix, if you find one, plz let me know, pvt message me the solution or a link back to this thread since its a bit hard to follow through on soo many threads.

Good Luck

-LuisGMarine

---

### Post by LuisGMarine on 2007-05-02
I tried this fix, which I thought I had on my system but there seemed to be something wrong with the code.  This fixed the problem for me, and I'm hoping it might do the same for you.

Open up terminal, and type this in:
```
sudo gedit /home/USERNAME/.fonts.conf
```

Of course, replace the 'USERNAME' with your actual user name.

Next, add this to the file:
```
<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

Hit the 'Save' button, log out , then restart X by doing the old ' ctrl + alt + backspace ', log back in and you should notice some big differences.  If not then keep looking, however this seemed to work for me just the way I wanted.

Good Luck

-LuisGMarine :guitar:

---

### Post by Lucifiel on 2007-05-02
To LuisGMarine :

Thank you for posting the fix. 

I tried it and however, it didn't solve the issue for me. Hmmm... if only I could narrow down the issue. T___T

---

### Post by Lucifiel on 2007-05-02
Oh wait, I finally decided to try tinkering around with the code LuisGMarine gave me and realised I'd just blindly copied and pasted the code. After removing the following code below in fonts.conf, I restarted X server and my fonts are now working!! :D

<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

---

### Post by LuisGMarine on 2007-05-03
> **Lucifiel said:**
> Oh wait, I finally decided to try tinkering around with the code LuisGMarine gave me and realised I'd just blindly copied and pasted the code. After removing the following code below in fonts.conf, I restarted X server and my fonts are now working!! :D

<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
Glad to see the code worked!

Good Luck

-LuisGMarine

---

### Post by Lucifiel on 2007-05-03
Yes!! :D There's nothing like the triumph of knowing you've fixed a problem. Although, really, this one got me. :P

---

### Post by Lucifiel on 2007-05-03
Looks like in the past 5 to 6 hours or so, the font in OpenOffice Writer was affected as well. Yeah, I didn't open Openoffice in the past 8 hours or so. 

Applying the subpixel = <edit name='autohint' mode='assign'> fix works for everything but OpenOffice. Removing the fix does nothing for Open Office. Hmmm...

---

### Post by LuisGMarine on 2007-05-03
Look around, there is another person on these forums that is having the same problem.  I think I saw them on that link you provided on updating the fonts.  I believe someone on there had problems with the Open Office fonts, and when they upgraded it fixed it for them.

Check it out and keep me posted!

---

### Post by Lucifiel on 2007-05-07
Yeah, I'll get around to looking at the Feisty fawn font thread soon. :)

---

### Post by rockhoppr on 2007-05-08
This fixed my issue as well though I'm not sure why. :)

Thanks for posting it!

---

### Post by herbster on 2007-09-09
I just applied the fix, logged back in and Firefox is definitely much clearer, whew. It seems to have slightly affected my Gnome text as well, I can't pinpoint it exactly but it looks the tiniest bit different, I'm going to keep using it for a while and see how it goes.

Thanks very much, this has been bothering the hell outta me since I got my LCDs.

---

### Post by herbster on 2007-09-09
Yup, this is amazing. This has fixed all my fonts in Firefox and even Gnome's fonts look better now. Amazing!! Thank you so much! :) :)

---

### Post by ndavenport on 2007-11-04
Absolutely fixed my problem!

Thanks

Edit:

After I restart my computer I lose the effect of .fonts.conf and Firefox goes back to broken.
To it fix I must "sudo touch .fonts.conf" and then restart X with ctrl-alt-bksp everytime I restart my computer.

It's a pain but at least it works.

---

