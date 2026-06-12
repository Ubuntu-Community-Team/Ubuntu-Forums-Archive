---
title: "I think i chown something now i can't update ubuntu!"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-05
Hi,

i did :
sudo chown -R James /usr/lib
sudo chown -R James /usr/share
sudo chown -R James /usr/bin

what where their original ownership?

how can i fix it?

thanks...

---

### Post by gazj on 2007-12-05
it would have been root

sudo chown -R root 'files'

---

### Post by hopelessone on 2007-12-05
thanks..

i'll give it a shot n report back... wish me luck...

---

### Post by hopelessone on 2007-12-05
ok..

did it..
do i have to reboot?

i have a problem for 3 days that i cant update Ubuntu... i have 32 updates to install...

what other causes would be the problem..?

i think the problem started when i did the chown command... but dunno...

what other things can i do to get it going?

thanks..

---

### Post by hyper_ch on 2007-12-05
WHY did you chown it at all to your user?

---

### Post by hopelessone on 2007-12-05
followed this to uninstall AWN

[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

---

### Post by ukripper on 2007-12-05
Not a very good security doing chown on root priveleged directories

---

### Post by hopelessone on 2007-12-05
security...Eeeeeeekk

what can i do to turn this around? or do i do a reinstall?

---

### Post by hyper_ch on 2007-12-05
somebody should point that out on that How-To that it is very bad practice chowning those "public" folders.

---

### Post by hopelessone on 2007-12-05
what would be the recommended action to fix my beaten up Ubuntu...

thanks

---

### Post by gazj on 2007-12-05
it's very bad practice to change the owner of anything that is not under /home

If changing them back to root hasn't fixed, a reinstall is all i can suggest unfortunately, it would probably be for the best if you haven't configured to much yet.

That how-to needs amending to stop this happening to others, i really can't see the point in the step to me?!?!

---

### Post by hyper_ch on 2007-12-05
unfortunately not all is totally owned by root in those dirs.

---

### Post by hyper_ch on 2007-12-05
I did report that howto to the mods

> 
In this howto the TO says for uninstalling that you have to chown /usr/lib /usr/share and /usr/bin to the current user. Someone followed that ([http://ubuntuforums.org/showthread.php?t=632110](http://ubuntuforums.org/showthread.php?t=632110)) and run in problems. I don't think chowning those folders is good practice and that should not be in a howto.


---

### Post by The Cog on 2007-12-05
I note that /usr/bin/at is suid daemon. I think that changing it to suid root instead would leave something of a security hole. Depending on what other applications are installed, chown -R root on those public directories could leave other problems too. 

I suggest that you reinstall.

---

### Post by PmDematagoda on 2007-12-05
I agree, a reinstall is your best bet.

---

### Post by hopelessone on 2007-12-05
OK 

live and learn...

will be cautious in the future what i am doing...

see you all in 20 mins after a re-install...

anyway learning linux is fun...i like it more and more everyday..

thanks for all you info helped heaps...

---

### Post by master5o1 on 2007-12-05
If you aren't quite sure what you are doing always ask :)

---

### Post by hyper_ch on 2007-12-05
> **master5o1 said:**
> If you aren't quite sure what you are doing always ask :)

If there's a howto that tells him to do that and that has been approved by the mods, why should he be unsure about it?

---

### Post by PmDematagoda on 2007-12-05
Agreed, and since so many people have been using that with no problems(Though not really getting the fact that they have made themselves insecure and their OS unstable) it would have gone undetected and everyone would think it is ok.

---

### Post by frodon on 2007-12-05
Users can alo edit posts after we approve them so we can't control everything and it is where your report hyper_ch is really imporatant and helps the community.

I have edited the post in question with a warning and PMed the author, thanks for your report it helps a lot.

Everyone who notice unsafe instructions please report them, it is the best way to help us.

---

### Post by master5o1 on 2007-12-05
> **hyper_ch said:**
> If there's a howto that tells him to do that and that has been approved by the mods, why should he be unsure about it?

I know that what I meant is if you don't know what the command you are doing does ask. Good way to learn.

---

### Post by ByteJuggler on 2007-12-05
You shouldn't really have to reinstall to fix that... what is the exact error you're getting when updating?

---

### Post by hopelessone on 2007-12-05
well since i got an hour to move stuff across to another HDD...

i don't get any error when i click install updates it just the same as the check button...no downloads just keeps checking...

+ i can't fire up Synaptic Manager...

---

### Post by gazj on 2007-12-05
> **frodon said:**
> Users can alo edit posts after we approve them so we can't control everything and it is where your report hyper_ch is really imporatant and helps the community.

I have edited the post in question with a warning and PMed the author, thanks for your report it helps a lot.

Everyone who notice unsafe instructions please report them, it is the best way to help us.

soory to be a pain, could you just move the warning up above the chown command, as it still looks like that is ik to be run.

Thanks :)

---

### Post by ByteJuggler on 2007-12-05
> **hopelessone said:**
> well since i got an hour to move stuff across to another HDD...

i don't get any error when i click install updates it just the same as the check button...no downloads just keeps checking...

+ i can't fire up Synaptic Manager...

OK, well open up a console window for me, then try:

```
sudo apt-get update
```

Please post back any errors that spits out.  (You can copy and paste from the terminal by marking the text with the mouse, then middle clicking (mouse wheel click or both left/right at the same time) in the window you want to paste into.)

---

### Post by nikoPSK on 2007-12-05
so they kill your sudo? Xrap, I had advised to use them in my guide but I guess I can find an alterte solution.

---

