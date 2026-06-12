---
title: "Rooting Kindle Fire 2nd gen version 10.2.4"
date: 2012-12-28
forum: Any Other OS
---

### Post by f1ndingwalden on 2012-12-28
As a gift I recently received a new Amazon Kindle fire, and after a quick google search I was exited to learn that it runs on android (although a very, *very* modified version. I quickly got sick of the device because it is basically a handheld billboard, completely uncustomizable, and since you dont have access to the android market, the apps suck. However, the hardware, for the most part (despite the fact that there is no micro sd card slot, microphone, bluetooth, or camera) is basically the same as a samsung (the display, RAM, and flash memory are all samsung), so I was determined to root the thing, and unleash its full potential. 

To my knowledge this is currently impossible if you are running linux/ubuntu. 
Below I will list every method that I have tried and each problem that I have hit, and hopefully somebody out there with a better knowledge of android can steer me in the right direction.

So one of the first things that came up after googleing how to root kindle was the Kindle Fire Utility. This thing was to good to be true. It didnt have a linux version, but I read somewhere that the only difference in syntax between the .bat files that it runs off of and the linux-friendly .sh files is that "cls" is replaced with "clear" and "del" is replaced with "rm". 
Not knowing much about either file type, I figured i'd go through and changed everything in the .bat files, then save them as .sh run chmod +x and execute them.
Not surprisingly, this dosnt work. 
I couldnt run them with wine either, so the only other thing I could think of is a virtual machine, which I dont have set up, but Im not even sure that this would work.

The next thing I tried was the freindly sounding superoneclick.
I downloaded and extracted it, ran the exe file and the program loads.. however it does not recognize anything at all and I cant change any settings in it whatsoever.
... so I found that I needed to edit the adb_usb.ini in the ~/.android folder and add 0x1949 and also edit the  /etc/udev/rules.d/60-android-adb.rules (instructions [[COLOR="Orange"]here[/COLOR]]("http://http://mjanja.co.ke/2012/02/using-adb-on-the-kindle-fire/")).
I also then needed to change the settings on the actual kindle (dropdown menu-> device-> allow installation of applications from unknown sources->yes and also dropdown menu-> security-> Enable ADB-> on).
This still didnt do the trick, but are all necessary steps to get adb to even recognize the device (run "adb devices" in a terminal and if it responds with a line of numbers and letters and the word device, then you know your golden).

Next I tried rootkindlelinux and followed the instructions from [[COLOR="DarkOrange"]here[/COLOR]]("http://http://rootkindlefire.com/kindle-fire-root/how-to-root-kindle-fire-for-mac-osx-or-linux/"), which in the end gave me a lovely "All Done, Kindle Fire ROOTED!!!", but didnt seem to actually do anything to kindle itself other than reboot it, and only then did i realize that this was for version 6.2.

After that I tried [[COLOR="rgb(255, 140, 0)"]this method[/COLOR]]("http://rootzwiki.com/topic/34162-root-kindlefire-7hd-probably-the-other-2ndgen-kindlefire/") which seemed really really promising.. but I shortly hit a few road bumps. 
Whenever I got to the part where I enter
>  $ echo 'ro.kernel.qemu=1' > /data/local.prop
I get a lovely 
> /system/bin/sh: cannot create /data/local.prop: Permission denied

so... I tried changing it to
> $ echo 'ro.kernel.qemu=1' > /data/local/temp.prop
which seemed to do the trick.. 
Until I tried 
> adb shell mount -o remount,rw /system

and got 
> mount: Operation not permitted

to which I could not find a workaround.

The next thing I tried was [[COLOR="rgb(255, 140, 0)"]this guide[/COLOR]]("http://alldroid.org/default.aspx?g=posts&t=493") where I was going steady until I hit >  "adb push exploid /sqlite_stmt_journals/exploid"

and received > failed to copy 'exploid' to '/sqlite_stmt_journal/exploid': No such file or directory
so i could never run exploid and was once again stumped. 

The last thing I tried was [[COLOR="rgb(255, 140, 0)"]this one.[/COLOR]]("http://forum.xda-developers.com/showthread.php?t=1886460") After I extracted it and ran the sh file I got a promising looking program, where I ran in "special mode" because it was a tablet, then selected root. While it was running after every command it said "Permission Denied" and even though the developer said that this was Ok and I even got a awesome "After reboot all is done! Have fun!" My Kindle was still not rooted. I ran it a few more times in both modes, but still nothing. 

I can't figure this one out, and would really appreciate some help if anyone can offer it. Sorry this post is so long, but I wanted to give someone else a heads up before they go down the same road that I did.

---

### Post by dave.tomkins on 2012-12-29
Hi,

After you tried to create the "local.prop" file on the kindle, it looks as though you weren't connected to the kindle, as your shell prompt was "$"

Here's the output from my shell (term) on my laptop:
[INDENT]**$** id
uid=1002(david) gid=1002(david) groups=1002(david),4(adm),6(disk),27(sudo),109(lpadmin),124(sambashare)
**$** pwd
/home/david
**$** echo $PS1
$
**$** 

[/INDENT]...now, when I open a shell on the kindle, (by running the "adb shell" command), things look a little different:

[INDENT]**$** adb shell
**shell@android:/** $ id          *<-- you can see that I have now connected to a shell on the kindle as the prompt has changed, along with the output of the "id" / "pwd" and "echo $PS1" commands*

uid=2000(shell) gid=2000(shell) groups=1003(graphics),1004(input),1007(log),1009(mount),1011(adb),1015(sdcard_rw),3001(net_bt_admin),3002(net_bt),3003(inet),3006(net_bw_stats)

**shell@android:/** $ pwd
/
**shell@android:/** $ echo $PS1
$(precmd)$USER@$HOSTNAME:${PWD:-?} $
[/INDENT]
Therefore, if you're failing to open the shell on the kindle, try issuing the following:

[INDENT]**$** adb kill-server
[/INDENT]...and then you should be able to connect to the kindle by issuing the "adb shell" command
i.e.

[INDENT]**$** adb shell
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
**shell@android:/ **$ 
[/INDENT]If you get this far, then you should be able to follow the instructions (as I did) from the link (“[[COLOR="rgb(255, 140, 0)"]this method[/COLOR]]("http://rootzwiki.com/topic/34162-root-kindlefire-7hd-probably-the-other-2ndgen-kindlefire/")”)   in your post.
...starting from the point where it says:

[INDENT]shell@android:/ $ rm -r /data/local/tmp
[/INDENT]...one final note, if the command fails for any reason, just check that there are no files in "/data/local/tmp" that you can't remove for any reason.

The following "ls" command (which will display a listing of the contents of the directory)  should come straight back to "**shell@android:/** $" prompt
i.e.  [INDENT]**shell@android:/** $ ls /data/local/tmp
**shell@android:/** $ 
[/INDENT]Hope this helps.

Dave

---

### Post by f1ndingwalden on 2012-12-29
Hey Dave, thanks for your reply..
When I do 
> shell@android:/ $ ls /data/local/tmp

I get 

> shell@android:/ $ ls /data/local/tmp
/data/local/tmp


So I then I tried and got this..
> shell@android:/ $ cd /data/local/tmp
shell@android:/data/local/tmp $ ls
opendir failed, Permission denied


Not sure what I am looking for with that though and why I don't have permission to go to that directory. Maybe I need root access? 

Also, I tried the method you listed again because after I rebooted the device I wasn't connecting to the shell properly like you had said, but then this happens 
> shell@android:/ $ echo 'ro.kernel.qemu=1' > /data/local.prop
/system/bin/sh: cannot create /data/local.prop: Permission denied


Any thoughts?

---

### Post by dave.tomkins on 2012-12-30
Hi,

I don't have access to my kindle at the moment - kids are playing games on it!!, and as I've got to go off and do some DIY today (aaargh!) I'm not going to get a lot of time investigating until later this afternoon/evening.

in the meantime, what version of "adb" are you running?

The version I am using is:

[INDENT]david@localhost $ adb version
Android Debug Bridge version 1.0.29
david@localhost $ 
[/INDENT]
The other thing you could do is take a look at your environment when you connect to the kindle (issue the "id" command after you run "adb shell")
...post the output...

Finally,  change directory ("cd /data/local/tmp") 
If this fails, then the "tmp" directory is not accessible for some reason (?!)
However, if you can "cd" to the "/data/local/tmp" directory, remove whatever is in there ( " rm ./* ")
...then change directory one level up (" cd .. ") and then remove the "tmp" directory:
 (" rmdir tmp ")

The only other thing I can possibly grasp at is you may need to execute the "adb" command with elevated privileges (" sudo adb shell ") 

Let me know how you get on, and I'll check back later - after I've drilled a few holes in the wall and undoubtedly hammered a nail or two through my thumb ;)

Cheers,

Dave

---

### Post by f1ndingwalden on 2012-12-30
Hey Dave, I really appreciate your help, and good luck with your diy project!

So Im running adb version 1.0.29 too, and the response to id is
> uid=2000(shell) gid=2000(shell) groups=1003(graphics),1004(input),1007(log),1009(mount),1011(adb),1015(sdcard_rw),3001(net_bt_admin),3002(net_bt),3003(inet),3006(net_bw_stats)


so I do have access to th tmp directory, however 

> shell@android:/ $ cd /data/local/tmp
shell@android:/data/local/tmp $ rm./*
/system/bin/sh: rm./*: not found


then when I try and delete the tmp dir I get this;

> shell@android:/data/local $ rmdir tmp
rmdir failed for tmp, Not a directory

..

I dont know why I tmp is not a directory.. maybe I created a file named tmp when I was messing around with it? ..Not really sure about that one.

Also when I try and ls in tmp I get 
    "shell@android:/data/local/tmp $ ls
     opendir failed, Permission denied"

So I tried it again after running sudo adb shell and got the same thing. Also tried all the other comands w/ sudo access and got the same responses.

Then I was curious what was in the local dir..
> 255|shell@android:/data/local $ ls
temp.prop
tmp
tmp.bak
tmp.prop
shell@android:/data/local $ 


Weird..
Any ideas?

Thanks again,
D

---

### Post by mamamia88 on 2012-12-30
do you mean the 7" original or the new kindle fire hd?   if you check the xda section for development it looks pretty dead.   are you sure that if you even rooted it that it would do you any good?   here is where you should go for the original [http://forum.xda-developers.com/forumdisplay.php?f=1309](http://forum.xda-developers.com/forumdisplay.php?f=1309)  here is for the hd [http://forum.xda-developers.com/forumdisplay.php?f=1786](http://forum.xda-developers.com/forumdisplay.php?f=1786) i would ask in the q&a section though.  you need to know what version you have first. if you can't find an answer on xda you won't find it anywhere

---

### Post by f1ndingwalden on 2012-12-30
Its definitely the 7".. and ill post my problems up there... and yeah there are a few ROMs i can put on it plus the google android market.

I really dig your Linus Torvalds quote by the way

---

### Post by Neon Lights on 2013-01-17
Did you ever find a solution? Having the same problem here.

---

### Post by f1ndingwalden on 2013-01-17
Nah man, not yet:/ 
Although I havnt had time to try in the past week so ill give a crack at it again when I get the chance, and if I d ill be sure to update this thread. Good luck, and keep me posted if you find an answer!
stupid amazon and all there security so they can put ford adds as my back ground. Its really a load of bs

---

### Post by dave.tomkins on 2013-01-23
[f1ndingwalden]("http://ubuntuforums.org/member.php?u=1716147") - soz - been away from this forum for a while, so was wondering how you are getting on with your kindle?

I just scanned back through your comment and noticed that you got a message when you entered the following:
   
   shell@android:/data/local/tmp $ rm./*
   /system/bin/sh:** rm./*: not found 			 		**

this means you missed the <space> between the "rm" and the "./*"
For info - "rm" is a command to remove (or delete) something, and the "./*" is telling the "rm" command  command to remove everything (*) that is in the current directory "./"
(BTW - I'm really sorry if that sounded patronizing, but I don't know how well versed you are with unix commands :neutral: )

Therefore, if you can get back to the "/data/local" directory on the kindle and keyin:

  ls 

...you should be given a listing of that directory, and you should be able to see if there is a file in there called "tmp"

...not sure of the kindle cannibalized o/s supports all the standard arguments to "ls", but you can always try "ls -l" or "ls -F" to get a more detailed view of the contents of the "/data/local/" directory.

Please post output.

Cheers,

Dave

---

### Post by f1ndingwalden on 2013-01-24
Hey Dave, 
So I was able to succesfully remove tmp, so that now when I run ls in /data/local I get

fbmode
nbmode
temp.prop
tmp.prop

however, when I run 

$  echo 'ro.kernel.qemu=1' > /data/local.prop

I get a lovely

/system/bin/sh: cannot create /data/local.prop: Permission denied

then, curious, I ran ls again in /data/local, and tmp was back!
so I figured that tmp.prop and temp.prop where prompts that created tmp if it is missing. so i removed them, as well as tmp..
However when I rebooted, and checked it again, tmp was still there! and that means I deleted two files that I have no clue what they did and for no reason!

anyways I tried removing tmp and continuing without rebooting and I still got
echo 'ro.kernel.qemu=1' > /data/local.prop
/system/bin/sh: cannot create /data/local.prop: Permission denied

Any ideas?

---

### Post by f1ndingwalden on 2013-02-22
Finally found something that works!
Gotta love xda.
[http://forum.xda-developers.com/showthread.php?t=2074565&nocache=1&z=8230618383346955](http://forum.xda-developers.com/showthread.php?t=2074565&nocache=1&z=8230618383346955)

---

### Post by madman420 on 2014-02-12
This site has a method that works with Kindle Fire 2nd generation, non-HD, non-HDX tablets:

staticchaos.freeoda.com/fire

It is Windows-only though.

---

