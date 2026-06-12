---
title: "I've done a horrible thing-stuck in Windows"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-05-26
I am a windows XP user. I installed Fiesty Ubuntu using Wubi. I've been working with it for several days now and I love it. Problem is, I tinkered with the xorg.confi using the procedure listed here [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471).
Now when I boot to Ubuntu, it doesn't like what I've done and fails to boot.
How can I edit the xorg.conf file now. All I need to do is restore it like it was and things should be fine.
Thanks for any help you can give me.:(

---

### Post by adt41287 on 2007-05-26
one thing i have learned after 'tinkering' with xorg.conf, always back up files!! :D

for future reference type this command in terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then to restore the original, do exactly the opposite:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

but to restore original what i did when i made this mistake was boot up with the Ubuntu live cd then copy (sudo cp /etc/X11/xorg.conf) to the file system you previously installed. hope this helps!

---

### Post by Ek0nomik on 2007-05-26
What do you mean by:  "fails to boot"?

Does it take you to a command line prompt?  If so, excellent!

If you remember the exact changes you made, than you can run this command to edit the file:

```
sudo nano /etc/X11/xorg.conf
```

Now you can edit the file, use Ctrl+O to write out to the file (save), and Ctrl+X to exit, than type:

```
sudo shutdown -r now
```

And you should be all set.  :)

---

### Post by MonkeyBoy on 2007-05-26
I am assuming it boots you to a command line?

If so try typing:

```
sudo dpkg-reconfigure xserver-xorg
```

This will start a simple gui for sorting out your Xorg.conf.  It asks about lots of hardware and then alters the xorg.conf afterwards.  

This should work I think.  #fingers crossed#

---

### Post by adt41287 on 2007-05-26
try Ek0nomik's suggestion first... if you do not have a command prompt hit ctrl+alt+F1 and it should take you to command line login....

if you dont remember what you did, mine suggestion worked just fine for me

---

### Post by stevelasvegas on 2007-05-26
No, I can not boot to the command line, even using ctrl+alt+F1.
Ubuntu begins to load. As the text lines are listed, it pauses at "running local boot scripts (/etc/rc.local).
Then it lists an error regarding the x server.
Then it continues and looks like it unloads everything.
Then the laptop powers down and turns off.
I am going to try to load Ubuntu from live CD and try to access the file. I edited it using rems (#) to rem out the existing mouse configuration by adding other text.
If I could just edit the xorg.conf fileI'd be in business.
Even after booting to the Ubuntu Live CD, will I be able to access the xorg.conf file? Will I have to "mount" the drives that are listed in the Wubi install (I don't even know how to do that).
No more sudo for me.
By the way, is there a Linux version of Windows System Restore that I could use to restore files?
Unbelievable how quickly you guys responded! Thanks so much.

---

### Post by paparucino on 2007-05-26
> **stevelasvegas said:**
> .
Even after booting to the Ubuntu Live CD, will I be able to access the xorg.conf file? Will I have to "mount" the drives that are listed in the Wubi install (I don't even know how to do that).

All what you need is to load the live CD, obtain a terminal and try one of the procedures stated above.
Personally I prefer dpkg-reconfig

> No more sudo for me.
By the way, is there a Linux version of Windows System Restore that I could use to restore files?

The only way is to save the config file related to the app you intend to modifiy.

> Unbelievable how quickly you guys responded! Thanks so much.
We are paid for this :lolflag:

---

### Post by stevelasvegas on 2007-05-26
I can see it but can't get to it :(
I booted to Ubuntu with the Live CD.
I am trying to access the xorg.conf file that I edited while in Ubuntu Feisty installed using WUBU.
I go to the DISKS folder.
In that folder are;
home.virtual.disk
swap.virtual.disk
system.virtual.disk
Using my Windows trained brain, I am thinking I want to access the files in the system.virtual.disk and then navigate to the xorg.conf file in  /etc/X11/ directory. Then edit the xorg.conf file.
How can I do that or at least modify or replace the file so Ubuntu can boot completely. Else, do I have to reinstall and start all over?
Thanks again.
One way or another I will get back to booting to Ubuntu because I love it.

---

### Post by stevelasvegas on 2007-05-26
Do you think this will work?
[http://ubuntuforums.org/showthread.php?t=436923&highlight=access+system.virtual.disk](http://ubuntuforums.org/showthread.php?t=436923&highlight=access+system.virtual.disk)

---

### Post by Toadmund on 2007-05-26
Use Ek0nomik's method, but get there by choosing recovery mode for your version in the grub menu, that will get you the command prompt.

---

### Post by Pizzarth on 2007-05-26
I thought it was F6 and not F1... that's what worked for me at least.

in the x windows error I'm guessing you're getting that blue and red screen? after going through the funky error messages it boots into command line anyway, but doesn't have a prompt right away, just type your name and then the password. or you could just put in wrong info till the [computer name] login part appears.

---

### Post by stevelasvegas on 2007-05-26
This is making me crazy. This is the kind of thing I used to do with Windows, spending the whole day trying to fix a little problem. I will never do this again. I'm still not out of the woods. I can read the file but can't write it. Back to the drawing board.

---

### Post by Pizzarth on 2007-05-26
maybe you can't write to it because you havent used sudo? or if you want, just temporarily become root then open the file normally. to do so type "sudo -s" and then it'll ask for your password. don't give up, you'd be missing out on a great system

---

### Post by stevelasvegas on 2007-05-26
Thank G_d (and all of you), I'm back in.
The problem was when I tried the ctrl+alt+f1 I was not presented with the username/password lines (or at least I didn't see it). After looking for a way to edit the file using programs that would mount the virtual.system.disk and blah, blah, blah. Wasting hours.
I should have taken a mood elevator and started over. I did the ctrl+alt+f1 again and saw the login text and then followed Ek0nomik's procedures.
That did it!
Although my frustration level was at a 9, my tenacity level was a 10 and with the help you guys gave me I was able to get back where everything is beautiful again.
Thank you all so much. Getting familiar with Linux looks like it's going to be a steep learning curve.
Thanks again. You are all great! :p

---

### Post by Toadmund on 2007-05-26
Heck man, Win98 was a steep learning curve for me (my first comp.), therefore Linux is easier than you think once you get used to it.
Happy for ya!

---

### Post by boudreaujr on 2007-05-26
Always try and stay calm.  If that fails, turn if off for awhile.  I broke my system today doing some security updates.  Had to reload my nvidia drivers through the recovery mode to get it working again.  You'll get used to controlling your system and will have fun doing it.  Just remember to stay calm.  People here will be more than willing to help but also try the search function to look for articles that fit your problem.  Chances are you have company in what you are doing and someone has already answered the problem.  Most of the time that is how I find my answers.  I love linux for many reasons.  Sometimes it is frustrating but still very rewarding in learning.

Good luck.

Denis

---

