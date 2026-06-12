---
title: "Grub Error 15 please help!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by yamswirl on 2007-04-18
Had a bit of a SNAFU.  I was trying to manually partition my external hard drive and it seemed like all was well and then I got an error message.  I don't remember what it was, something about not being able to complete.  After that anything I tried to do in System and Applications gave me an error message so I tried to restart.  Well, the restart hung up so I did a hard shut down and now I'm getting a grub error 15 message as soon as I turn the computer on.

Does this mean I've lost everything and have to start over or is there something I can fix to make it start again?  Right now all I can do is boot from the disc.

I'm using Dapper and a Gateway laptop. 
Please help! Please.:sad:

---

### Post by Bachstelze on 2007-04-18
When you run GParted from the Live CD, does it detect the partitions or does it see the drive as "unformatted" ?

---

### Post by yamswirl on 2007-04-18
It's showing ext3, extended, and linux-swap.  ext3 has 6.89 of used space the status says unmounted.

---

### Post by prince_niceguy on 2007-04-18
once you have booted try installing grub again. this should fix the issue.

---

### Post by Bachstelze on 2007-04-18
Maybe your GRUB was somehow confused, try to reinstall it :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by yamswirl on 2007-04-18
I'm new.  So am I looking at Recovering Grub in the Ubuntu link?  I'm only running Ubuntu on  my laptop if that makes any difference.

---

### Post by Bachstelze on 2007-04-18
You can use section 1.2 "Using the Desktop/LiveCD and Overwriting the Windows bootloader". It is in fact not specific to dual-boot systems, it will just reinstall GRUB and wipe out whatever was there before, that's what you want.

---

### Post by yamswirl on 2007-04-18
In step one I'm getting this, 

ubuntu@ubuntu:~$ sudo fdisc -l
bash: fdisc: command not found

---

### Post by Bachstelze on 2007-04-18
Try with *fdisk* instead ;)

---

### Post by yamswirl on 2007-04-18
Hehe.  The brain doesn't work so well at 3am.  :)  I read that line at least 10 times and saw the same wrong thing each time.

I'm gonna get some coffee and try this again.

---

### Post by yamswirl on 2007-04-18
Hey, when you enter stuff right it works much better!

But now I'm getting this:

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount -t ext3 /dev/sda1 mnt/root
mount: mount point mnt/root does not exist
root@ubuntu:~#

It claims that I have the mnt/root directory.  Do I need to move to that directory or something?
sigh...  also, what's the command to get out of root?  I don't want to bung anything else up.  At least not till I get done with this.

---

### Post by yamswirl on 2007-04-18
So does anyone know if I will loose all my files if i reinstal Ubuntu?  The files appear to still be there but I don't know how to get to them.

I'm still stuck with this Grub Error 15...

help...:icon_frown:

---

### Post by freebird54 on 2007-04-18
Here is a link explaining all you;ll need to know about Grub, and recovery from partition troubles.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There is a table of contents - you don't need the whole thing!

---

### Post by yamswirl on 2007-04-18
So is, "Re-installing GRUB using Rescue mode in the 'Alternate Install' CD" what I'm looking for?

There is no option to rescue a broken system on my cd.  So if I try to do it from the command line with [FONT="Lucida Console"]grub>c [/FONT]  it says [FONT="Lucinda Console"]Probing devices to guess BIOS drives.  This may take a long time.[/FONT]

This should probably be nice and easy but I feel like I might as well be reading all of this in Latin for as much sense as it's making to me.  And I kinda want to cry a little.:cry:

---

### Post by freebird54 on 2007-04-18
Actually I meanr Re-install Grub with a GRUB shell eg; with Live CD.................................................................. - but it depends on which CD you have.  It looks like a big task at first read-thru - but just do 1 thing at a time - pasting things in where possible (most of them are possible).

All you are doing is identifying where the grub should do, then telling it to go there.  It really isn't that bad - there's even pictures :)

Oh - and if you 'mess up' with those instructions - it won't be any worse than it is now.  That's a relief, right?

We're all still here.... (at least til the game gets going)

---

### Post by yamswirl on 2007-04-18
Yay for support and hockey!  I assume that's the game you mean.  But isn't tonight New Jersey and Tampa?

So, I tried [FONT="Courier New"]mount -t ext3 /dev/sda1 /mnt/root[/FONT] and got:

[FONT="Courier New"]mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error[/FONT]

So when I entered [FONT="Courier New"]dmesg | tail[/FONT] the only thing that looks wrong to me is [FONT="Courier New"]EXT3- fs: journal inode is deleted[/FONT]

I'm at work till 9 so I'll look at the link you sent again.  Does any of the above mean anything helpful?

---

### Post by yamswirl on 2007-04-18
Looks like I should change that to Yay support and Basketball!  Maybe...

---

### Post by freebird54 on 2007-04-18
Well - the support in hockey is appropriate - and you are righ about one the games on tonight.  However, the Blue jays are also there to take up the slack!  B-Ball- oh well.

Could we see the actual output from

sudo fdisk -l

It would helpo us to be sure what's going on here...

---

### Post by yamswirl on 2007-04-18
This might look not as neat as a cut n paste.  I'm at work and our wireless won't let me on so I'll have to re-create what I'm getting.  So here it is

Device Boot           Start             End                Blocks            ID               System
/dev/sda1  *                1          14219         114214086        83                Linux   
/dev/sda2            14220          14593              3004155         5                Extended
/dev/sda5            14220          14593              3004123+    82                Linux swap / Solaris


My first guess was hockey because the playoffs are going on.  I really really appreciate the help.  If I could've found a job in Toronto and defected to Canada this could potentially be going much more quickly.

---

### Post by captainbeah on 2007-04-18
Try jumping your BIOS. This will reset all of its settings, and hopefully kick it into shape. It isn't exactly easy though. You have to open up your computer, move a little bit of plastic from one pin to another, hold it there for a little while, and then put it back again. The exact instructions depend on your computer (really your motherboard). If this is too much work, that's ok. It worked for me, anyways.

---

### Post by yamswirl on 2007-04-18
Ok, that was a wicked mess.  Sorry.  Let me give you that a bit differently so you can at least read the numbers.  Stupid non working wireless connection at work.

Under Device I have:
/dev/sda1
/dev/sda2
/dev/sda5

The rest of the info for sda1 is:
Boot *, Start 1, End 14219, Blocks 114214086, Id 83, System Linux

sda2:
Start 14220, End 14593, Blocks 3004155, Id 5, System Extended

sda5:
Start 14220, End 14593, Blocks 3004123+, Id 82, System Linux swap / Solaris

---

### Post by yamswirl on 2007-04-18
Even better:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

```

finally got onto our wireless.

---

### Post by freebird54 on 2007-04-18
Ok - it is possible to get that error 2 ways. One is that grub is not properly installed - the other is that whatever it is trying to boot is not there.  More likely the first is the problem here,  I think.

Definitely the procedure to try is the **Re-install Grub with Live CD**.

4 stages.  Start grub:

```
sudo grub
```

check where grub part 1 is (the stuff in *italics* is a prompt -  type only the rest of the line

```
*grub>* find /boot/grub/stage1
```

probably returns (hd0,0)  then

```
*grub>* root (hd0,0)
```

sets grub 'working zone'  If it returned (hd0,1) then use that instead

```
*grub>* setup (hd0)
```

it sets things up for that root/drive.  SHould return something like

 ```
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)0+15 p (hd0,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

CLear enough.  If it worked, you should be able to shut down and reboot.

```
*grub>* quit
```

Let us know if it worked for you

---

### Post by yamswirl on 2007-04-18
I've tried that.  I can get in to the grub.  At step two I get
```
Error 15: File not found
```

I hate Error 15.:x 

Is the game done?  How'd it go?

---

### Post by freebird54 on 2007-04-18
Well - I was watching 3 of them :)  Blue Jays lost :(  Hockey series continue (only care to see who Flames meet if they survive - 'cos my Maple Leafs are already out.

I don't like your results - it suggests the other reason for problems - like the kernel files aren't as described in the menu.lst  Can you extract/post the file  /boot/grub/menu.lst from the drive  -- mount it from Live CD, then 

```
cat /boot/grub/menu.lst
```

---

### Post by yamswirl on 2007-04-18
sigh.  I don't like the results either.

I may not have entered this right but here's what I'm looking at.
```
ubuntu@ubuntu:~$ file /boot/grub/menu.lst
/boot/grub/menu.lst: ERROR: cannot open `/boot/grub/menu.lst' (No such file or directory)

```

Sorry 'bout the Maple Leafs.  And the Blue Jays.  Still watching one game?

---

### Post by yamswirl on 2007-04-18
And if I do it in Grub, where I was probably supposed to be, I get this:

```
grub> find /boot/grub/menu.lst

Error 15: File not found

```

---

### Post by freebird54 on 2007-04-18
Enough with the games - back to the work :)  Well - what command did you use to mount the drive?  It's acting like there's nothing there at all !! (we can't have that)  If

sudo mount /dev/sda1

does not give you more, we'll have to try the fsck (filesystem repair) tool next... (sigh)

---

### Post by freebird54 on 2007-04-18
OOps - you're still in grub!  We need you in a terminal for these other commands!  It is so hard to see what you're doing from here :)  enter **quit** at the *grub> *prompt....

Try the mount command from an Applications->Accessories->Terminal wndow, then the cat command that I posted earlier.  We can hope again!

---

### Post by yamswirl on 2007-04-18
sigh indeed.
Ok, I tried this
```
mkdir /mnt/root

mount -t ext3 /dev/sda1 /mnt/root 
```

it didn't work.  I can't remember in what way and now I'm getting different no good messages.
If I sudo mount /dev/sda1 I get
```
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

Now, just for clarification, where should I be?  Grub?  Root?  Home?  I've been staring at this all day.  Well at least since 1pm.

You're my new hero.

---

### Post by yamswirl on 2007-04-18
Found the error from mount -t ext3...

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing code page or other error. In some cases usefil info is found in syslog - try dmesg | tail or so
```

So I did mesg | tail and got 
```
EXT3-fs: journal inode deleted
```

I don't know what it means but it doesn't really sound good.

---

### Post by yamswirl on 2007-04-18
That's it, I'm moving to Canada.

So here's what the last set of commands looks like

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

```

it's all learning right?  I'll be so much wiser after this.

---

### Post by freebird54 on 2007-04-18
My bad - forgot there was no HD filesystem there for a minute :oops:

umm - got to look it up in here somewhere....

```
sudo mkdir /mnt/ubuntu
```
```

sudo mount -t ext3  /dev/sda1 /mnt/ubuntu
```

THEN you can run the commands!  Ok?

---

### Post by yamswirl on 2007-04-18
Grr!  In theory.
```
mount: unknown filesystem type 'ext'
```

So I cut and pasted and:
```
ubuntu@ubuntu:~$ sudo mount -t ext3  /dev/sda1 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

:cry:

---

### Post by freebird54 on 2007-04-19
Let me look back on that sudo fdisk -l output!  It SHOULD have been ok... (pause)

Hmm - have you tried the syslog command?  DId it tell you anything?  This is getting a bit strange for me!  Hang on while i do some research.... (or let me know if you want to give up for now).  It must have happened before somewhere....

---

### Post by freebird54 on 2007-04-19
OK - we will have to pull out the heavy hitters :)

```
e2fsck -C0 -f /dev/sda1
```

This is the equivalent of a scandisk on windows, or CHKDSK on Windows/DOS if you go back far enough.  I am told you answer yes to most of the questions it will ask you at the end, but I have rarely seen any problems myself so I don't know what the questions are.  if you aren't sure of the answers, post the question back here and I'll give you an informed opinion :)

OK?

EDIT:  THe places i tracked the error to, the other problems were solved this way :)

---

### Post by yamswirl on 2007-04-19
Not to be all high maintence but how do I run syslog and what would I be looking for in it?

Is it System>Administration>System Log?

---

### Post by freebird54 on 2007-04-19
Try the e2fsck first.** If** it doesn't work (hopefully unlikely) then we'll use the dmesg cmd etc...

---

### Post by yamswirl on 2007-04-19
Ok, here we go.

```
Deleted inode 3703116 has zero dtime.  Fix<y>?
```

Yes?

---

### Post by freebird54 on 2007-04-19
Unless it sounds ***_REALLY_*** scary - let it fix the problems...

EDIT:  That means (Y)es...

---

### Post by yamswirl on 2007-04-19
this one makes me a bit nervous
```
Entry 'update-dev' in /??? (1507329) has deleted/unused inode 1507405.  Clear<y>?
```

---

### Post by freebird54 on 2007-04-19
Yup,  Basically it is saying that a file entry has claimed disk space that has nothing in it.  Clearing it will allow that space to be used again as needed...

---

### Post by yamswirl on 2007-04-19
Ok.  Continuing with the Homer Simpson approach and hitting Y.  

Any key?  Where's the any key? :)

---

### Post by freebird54 on 2007-04-19
Its the big WIDE one at the bottom!  (works, after all)  They don't put a label on it because you use it so much....

---

### Post by yamswirl on 2007-04-19
should there be 10 million unused inodes?

---

### Post by freebird54 on 2007-04-19
I would say that needs to be fixed.  How big was the empty space before you started?  THis is going to make the filesystem work - but it is NOT guaranteed to preserve everything - just make what is saved accessible.

I hope it isn't asking you hit a key for EACH of them??

---

### Post by yamswirl on 2007-04-19
well, there was 6 something of used space and 100 something unused.  And yes, it's asking me to hit Y for EACH thing.  

Ow.  My finger.

---

### Post by freebird54 on 2007-04-19
Is THAT what they meant when they said a LOT of questions...  How are you with your toes?  Alternate, use the eraser end of a pencil - whatever...  No wonder it wouldn't mount!
Did you have a bad shutdown or power failure or something?

---

### Post by yamswirl on 2007-04-19
Oooh, ya know.  I was trying to be all smart and manually partition my external hard drive.  It didn't work.  Still not sure how it carped all over my laptop though.

---

### Post by yamswirl on 2007-04-19
So are you still gonna be here for a while or will this have to be continued tomorrow.  If you're still willing to see this to the end that is.

---

### Post by freebird54 on 2007-04-19
I seem to be here for a while yet.  As for how - my bet is that the wrong drive was selected just ONCE for an partition operation... :)

My answer may be a bit slower for while - got to see how bad the 'Feisty Fever' is!!  I'm not going near a Feisty server for a week!

---

### Post by yamswirl on 2007-04-19
need one of these to sit on the keyboard and hit Y.
[http://www.drinkingbirdshop.com/](http://www.drinkingbirdshop.com/)

---

### Post by freebird54 on 2007-04-19
I think they are too slow - if I remember rightly from my childhood!

---

### Post by yamswirl on 2007-04-19
turns out you can just hold down Y.

Still going...

Never drink and partition.

---

### Post by yamswirl on 2007-04-19
Sweet Fanny Adams!  That was BRUTALLY long.

This is the message at the end
```
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 30018/14286848 files (2.4% non-contiguous), 995135/28553521 blocks

```

---

### Post by freebird54 on 2007-04-19
It must have been - you outlasted me after all!  At least it *DID* end.  Hopefully you'll let me know if it mounts and/or boot now?

---

### Post by yamswirl on 2007-04-19
It does not.  I start the computer and get Grub Error 15.](*,)

---

### Post by freebird54 on 2007-04-19
OK - we know that.  BUT we need to know if it mounts - so that the fixes we tried before can run.  Before those fixes could not work because the drive was in a non-functional state....

Backtrack a little bit - and try the fixes.  We still have hope!

---

### Post by yamswirl on 2007-04-19
ok.  Am I going back to page 3 in here, the grub step by step or just the mkdir mount part?

---

### Post by freebird54 on 2007-04-19
Lets get it mounted first - then we can see if it need more grub :)

---

### Post by yamswirl on 2007-04-19
No error message.  That's good, right?

I'm here:

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3  /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$

```

---

### Post by freebird54 on 2007-04-19
Absolutely!  Now - what do you want to ty first? maybe 

```
ls /boot/grub
```

and see what's in there?  Or just go through the fixes in the *grub>* environment directly?

---

### Post by yamswirl on 2007-04-19
I tried ```
ubuntu@ubuntu:~$ ls /boot/grub
ls: /boot/grub: No such file or directory

```

Will the steps to fix grub take care of that?

---

### Post by freebird54 on 2007-04-19
We hope so.  the setup should create parts of that.  (assuming the /boot/directory is still there!)

Give it a try anyway - if not then we'll have to see what *IS* there...

---

### Post by yamswirl on 2007-04-19
D'oh!

```
grub> find /boot/grub/stage1

Error 15: File not found

grub>

```

---

### Post by freebird54 on 2007-04-19
ok.  First 

```
cd /mnt/ubuntu
```

```
ls
```

If you don't get anything - panic.  Otherwise try

```
ls boot/grub
```

I have to keep remembering things that would 'obvious' if I were there.  Sorry - slow today!

---

### Post by yamswirl on 2007-04-19
```
ubuntu@ubuntu:~$ cd /mnt/ubuntu
ubuntu@ubuntu:/mnt/ubuntu$ ls
lost+found
ubuntu@ubuntu:/mnt/ubuntu$ ls boot/grub
ls: boot/grub: No such file or directory

```

Am I doing this in the right place?  How long would it take me to drive to Toronto...

---

### Post by freebird54 on 2007-04-19
I am afraid you are in the right place, and not much is being seen.  Try an 

```
ls -la  lost+found
```

and see what's in there.  It does NOT look good though.  Perhaps 10 million inodes were indeed a problem....

---

### Post by yamswirl on 2007-04-19
That returned a bunch of stuff.  I don't know what any of it means.  I don't think this is all of it but don't know the code to get to the very beginning.  If you want to have a go:
```
-rw-r--r--   1 root root       44500 2007-03-13 21:29 #5001639
-rw-r--r--   1 root root       59050 2007-03-13 21:29 #5001640
-rw-r--r--   1 root root       89155 2007-03-13 21:29 #5001641
-rw-r--r--   1 root root       90592 2007-03-13 21:29 #5001642
-rw-r--r--   1 root root       38894 2007-03-13 21:29 #5001643
-rw-r--r--   1 root root       72756 2007-03-13 21:29 #5001644
-rw-r--r--   1 root root       49588 2007-03-13 21:29 #5001645
-rw-r--r--   1 root root      116647 2007-03-13 21:29 #5001646
-rw-r--r--   1 root root      221657 2007-03-13 21:29 #5001647
-rw-r--r--   1 root root       75096 2007-03-13 21:29 #5001648
-rw-r--r--   1 root root       38721 2007-03-13 21:29 #5001649
-rw-r--r--   1 root root       12703 2007-03-13 21:29 #5001650
-rw-r--r--   1 root root       63327 2007-03-13 21:29 #5001651
-rw-r--r--   1 root root      255803 2007-03-13 21:29 #5001652
-rw-r--r--   1 root root      229386 2007-03-13 21:29 #5001653
-rw-r--r--   1 root root        5602 2007-03-13 21:29 #5001654
-rw-r--r--   1 root root        6754 2007-03-13 21:29 #5001655
-rw-r--r--   1 root root        6467 2007-03-13 21:29 #5001656
-rw-r--r--   1 root root        7208 2007-03-13 21:29 #5001657
-rw-r--r--   1 root root        7324 2007-03-13 21:29 #5001658
-rw-r--r--   1 root root        6750 2007-03-13 21:29 #5001659
-rw-r--r--   1 root root        6750 2007-03-13 21:29 #5001660
-rw-r--r--   1 root root        6463 2007-03-13 21:29 #5001661
-rw-r--r--   1 root root        6463 2007-03-13 21:29 #5001662
-rw-r--r--   1 root root        6463 2007-03-13 21:29 #5001663
-rw-r--r--   1 root root        6176 2007-03-13 21:29 #5001664
-rw-r--r--   1 root root        7037 2007-03-13 21:29 #5001665
-rw-r--r--   1 root root        7324 2007-03-13 21:29 #5001666
-rw-r--r--   1 root root        7611 2007-03-13 21:29 #5001667
-rw-r--r--   1 root root        7324 2007-03-13 21:29 #5001668
-rw-r--r--   1 root root        7037 2007-03-13 21:29 #5001669
-rw-r--r--   1 root root        7324 2007-03-13 21:29 #5001670
-rw-r--r--   1 root root        6750 2007-03-13 21:29 #5001671
-rw-r--r--   1 root root        6463 2007-03-13 21:29 #5001672
-rw-r--r--   1 root root        6343 2007-03-13 21:29 #5001673
-rw-r--r--   1 root root       83563 2007-03-13 21:29 #5001674
-rw-r--r--   1 root root      129423 2007-03-13 21:29 #5001675
-rw-r--r--   1 root root      152229 2007-03-13 21:29 #5001676
-rw-r--r--   1 root root      106615 2007-03-13 21:29 #5001677
-rw-r--r--   1 root root        7281 2007-03-13 21:29 #5001678
-rw-r--r--   1 root root        5618 2007-03-13 21:29 #5001679
-rw-r--r--   1 root root        6196 2007-03-13 21:29 #5001680
-rw-r--r--   1 root root        6196 2007-03-13 21:29 #5001681
-rw-r--r--   1 root root        6196 2007-03-13 21:29 #5001682
-rw-r--r--   1 root root        6192 2007-03-13 21:29 #5001683
-rw-r--r--   1 root root        6192 2007-03-13 21:29 #5001684
-rw-r--r--   1 root root        6192 2007-03-13 21:29 #5001685
-rw-r--r--   1 root root        6192 2007-03-13 21:29 #5001686
-rw-r--r--   1 root root        5905 2007-03-13 21:29 #5001687
-rw-r--r--   1 root root        6479 2007-03-13 21:29 #5001688
-rw-r--r--   1 root root        5905 2007-03-13 21:29 #5001689
-rw-r--r--   1 root root        6754 2007-03-13 21:29 #5001690
-rw-r--r--   1 root root        3651 2007-03-13 21:29 #5001691
-rw-r--r--   1 root root        6754 2007-03-13 21:29 #5001692
-rw-r--r--   1 root root        3358 2007-03-13 21:29 #5001693
-rw-r--r--   1 root root      121313 2007-03-13 21:29 #5001694
-rw-r--r--   1 root root       14815 2007-03-13 21:29 #5001695
-rw-r--r--   1 root root        5140 2007-03-13 21:29 #5001696
-rw-r--r--   1 root root       11919 2007-03-13 21:29 #5001697
-rw-r--r--   1 root root      297067 2007-03-13 21:29 #5001698
-rw-r--r--   1 root root       18607 2007-03-13 21:29 #5001699
-rw-r--r--   1 root root       10806 2007-03-13 21:29 #5001700
-rw-r--r--   1 root root       73499 2007-03-13 21:29 #5001701
-rw-r--r--   1 root root       50086 2007-03-13 21:29 #5001702
-rw-r--r--   1 root root       39311 2007-03-13 21:29 #5001703
-rw-r--r--   1 root root       97831 2007-03-13 21:29 #5001704
-rw-r--r--   1 root root       81324 2007-03-13 21:29 #5001705
-rw-r--r--   1 root root      102393 2007-03-13 21:29 #5001706
-rw-r--r--   1 root root       16018 2007-03-13 21:29 #5001707
-rw-r--r--   1 root root      654715 2007-03-13 21:29 #5001708
-rw-r--r--   1 root root        3566 2007-03-13 21:29 #5001709
-rw-r--r--   1 root root        3518 2007-03-13 21:29 #5001710
-rw-r--r--   1 root root        4172 2007-03-13 21:29 #5001711
-rw-r--r--   1 root root        9818 2007-03-13 21:29 #5001712
-rw-r--r--   1 root root        4168 2007-03-13 21:29 #5001713
-rw-r--r--   1 root root        5717 2007-03-13 21:29 #5001714
-rw-r--r--   1 root root        3758 2007-03-13 21:29 #5001715
-rw-r--r--   1 root root       24442 2007-03-13 21:29 #5001716
-rw-r--r--   1 root root       25535 2007-03-13 21:29 #5001717
-rw-r--r--   1 root root       44889 2007-03-13 21:29 #5001718
-rw-r--r--   1 root root       11867 2007-03-13 21:29 #5001719
-rw-r--r--   1 root root       26856 2007-03-13 21:29 #5001720
-rw-r--r--   1 root root       31443 2007-03-13 21:29 #5001721
-rw-r--r--   1 root root        8357 2007-03-13 21:29 #5001722
-rw-r--r--   1 root root       71247 2007-03-13 21:29 #5001723
-rw-r--r--   1 root root       60611 2007-03-13 21:29 #5001724
-rw-r--r--   1 root root       19880 2007-03-13 21:29 #5001725
-rw-r--r--   1 root root       24763 2007-03-13 21:29 #5001726
-rw-r--r--   1 root root       38667 2007-03-13 21:29 #5001727
-rw-r--r--   1 root root       31230 2007-03-13 21:29 #5001728
-rw-r--r--   1 root root       47714 2007-03-13 21:29 #5001729
-rw-r--r--   1 root root       17804 2007-03-13 21:29 #5001730
-rw-r--r--   1 root root       63372 2007-03-13 21:29 #5001731
-rw-r--r--   1 root root        3111 2007-03-13 21:29 #5001732
-rw-r--r--   1 root root        5078 2007-03-13 21:29 #5001733
-rw-r--r--   1 root root        4008 2007-03-13 21:29 #5001734
-rw-r--r--   1 root root        3749 2007-03-13 21:29 #5001735
-rw-r--r--   1 root root        3748 2007-03-13 21:29 #5001736
-rw-r--r--   1 root root        3851 2007-03-13 21:29 #5001737
-rw-r--r--   1 root root        3815 2007-03-13 21:29 #5001738
-rw-r--r--   1 root root        5480 2007-03-13 21:29 #5001739
-rw-r--r--   1 root root        2987 2007-03-13 21:29 #5001740
-rw-r--r--   1 root root        2982 2007-03-13 21:29 #5001741
-rw-r--r--   1 root root        2993 2007-03-13 21:29 #5001742
-rw-r--r--   1 root root        3775 2007-03-13 21:29 #5001743
-rw-r--r--   1 root root        3612 2007-03-13 21:29 #5001744
-rw-r--r--   1 root root        4530 2007-03-13 21:29 #5001745
-rw-r--r--   1 root root        8593 2007-03-13 21:29 #5001746
-rw-r--r--   1 root root        5576 2007-03-13 21:29 #5001747
-rw-r--r--   1 root root        3651 2007-03-13 21:29 #5001748
-rw-r--r--   1 root root        4161 2007-03-13 21:29 #5001749
-rw-r--r--   1 root root        4196 2007-03-13 21:29 #5001750
-rw-r--r--   1 root root       27036 2007-03-13 21:29 #5001751
-rw-r--r--   1 root root       42422 2007-03-13 21:29 #5001752
-rw-r--r--   1 root root       23778 2007-03-13 21:29 #5001753
-rw-r--r--   1 root root       17789 2007-03-13 21:29 #5001754
-rw-r--r--   1 root root       68256 2007-03-13 21:29 #5001755
-rw-r--r--   1 root root        3348 2007-03-13 21:29 #5001756
-rw-r--r--   1 root root       98745 2007-03-13 21:29 #5001757
-rw-r--r--   1 root root        5382 2007-03-13 21:29 #5001758
-rw-r--r--   1 root root       18505 2007-03-13 21:29 #5001759
-rw-r--r--   1 root root       42191 2007-03-13 21:29 #5001760
-rw-r--r--   1 root root        4025 2007-03-13 21:29 #5001857
-rw-r--r--   1 root root        2996 2007-03-13 21:29 #5001858
-rw-r--r--   1 root root        3458 2007-03-13 21:29 #5001859
-rw-r--r--   1 root root        5923 2007-03-13 21:29 #5001860
-rw-r--r--   1 root root        5870 2007-03-13 21:29 #5001861
-rw-r--r--   1 root root       11175 2007-03-13 21:29 #5001862
-rw-r--r--   1 root root        4253 2007-03-13 21:29 #5001863
-rw-r--r--   1 root root        6132 2007-03-13 21:29 #5001864
-rw-r--r--   1 root root        9254 2007-03-13 21:29 #5001865
-rw-r--r--   1 root root       10284 2007-03-13 21:29 #5001866
-rw-r--r--   1 root root       16808 2007-03-13 21:29 #5001867
-rw-r--r--   1 root root       11262 2007-03-13 21:29 #5001868
-rw-r--r--   1 root root      306687 2007-03-13 21:29 #5001869
-rw-r--r--   1 root root       14388 2007-03-13 21:29 #5001870
-rw-r--r--   1 root root       29876 2007-03-13 21:29 #5001871
-rw-r--r--   1 root root        4159 2007-03-13 21:29 #5001872
-rw-r--r--   1 root root       10589 2007-03-13 21:29 #5001873
-rw-r--r--   1 root root        3675 2007-03-13 21:29 #5001874
-rw-r--r--   1 root root        3347 2007-03-13 21:29 #5001875
-rw-r--r--   1 root root        7419 2007-03-13 21:29 #5001876
-rw-r--r--   1 root root        3687 2007-03-13 21:29 #5001877
-rw-r--r--   1 root root        4091 2007-03-13 21:29 #5001878
-rw-r--r--   1 root root        3562 2007-03-13 21:29 #5001879
-rw-r--r--   1 root root        3607 2007-03-13 21:29 #5001880
-rw-r--r--   1 root root        3693 2007-03-13 21:29 #5001881
-rw-r--r--   1 root root        4091 2007-03-13 21:29 #5001882
-rw-r--r--   1 root root        3459 2007-03-13 21:29 #5001883
-rw-r--r--   1 root root        4088 2007-03-13 21:29 #5001884
-rw-r--r--   1 root root        3168 2007-03-13 21:29 #5001885
-rw-r--r--   1 root root        4021 2007-03-13 21:29 #5001886
-rw-r--r--   1 root root        3471 2007-03-13 21:29 #5001887
-rw-r--r--   1 root root        3162 2007-03-13 21:29 #5001888
drwxr-xr-x  11 root root        4096 2007-04-16 02:47 #5668865
-rwxr-xr-x   1 root root       28128 2006-08-02 12:04 #7028737
-rwxr-xr-x   1 root root       57092 2006-08-02 12:04 #7028738
-rwxr-xr-x   1 root root       31948 2006-08-02 12:04 #7028739
-rwxr-xr-x   1 root root       43400 2006-08-02 12:04 #7028740
-rwxr-xr-x   1 root root       33120 2006-08-02 12:04 #7028741
-rwxr-xr-x   1 root root       24120 2006-08-02 12:04 #7028742
-rwxr-xr-x   1 root root       72500 2006-08-02 12:04 #7028743
-rwxr-xr-x   1 root root       46292 2006-08-02 12:04 #7028744
-rwxr-xr-x   1 root root       60780 2006-08-02 12:04 #7028745
-rwxr-xr-x   1 root root       39332 2006-08-02 12:04 #7028746
-rwxr-xr-x   1 root root       21364 2006-08-02 12:04 #7028747
-rwxr-xr-x   1 root root       39812 2006-08-02 12:04 #7028748
-rwxr-xr-x   1 root root        7456 2006-08-02 12:04 #7028749
-rwxr-xr-x   1 root root       47736 2006-08-02 12:04 #7028750
-rwxr-xr-x   1 root root       35400 2006-08-02 12:04 #7028751
-rwxr-xr-x   1 root root       73084 2006-07-31 21:09 #7094273
-rwxr-xr-x   1 root root      106308 2006-06-16 15:59 #7176193
-rw-r--r--   1 root root       24144 2006-06-16 15:59 #7176194
drwxr-xr-x 109 root root        4096 2007-04-18 04:32 #8077313
-rw-r--r--   1 root root         577 2006-05-29 23:43 #8077699
-rw-r--r--   1 root root         506 2006-05-29 23:43 #8077700
-rw-r--r--   1 root root        4081 2006-05-18 09:47 #8077996
-rw-r--r--   1 root root        4893 2006-05-18 09:47 #8077997
-rwxr-xr-x   1 root root         559 2006-07-05 13:00 #8078852
-rwxr-xr-x   1 root root        2124 2006-02-23 16:37 #8078853
-rwxr-xr-x   1 root root         891 2006-07-05 13:00 #8078854
-rwxr-xr-x   1 root root        3940 2006-02-23 16:37 #8078855
-rw-r-----   1 root dip         1093 2006-08-05 23:24 #8078856
-rw-r--r--   1 root root          30 2006-05-25 21:47 #8078857
-rw-r--r--   1 root root          75 2006-05-25 21:47 #8078858
drwxr-xr-x   2 root root        4096 2007-04-13 06:38 #8079586
-rw-r--r--   1 root root        1512 2005-12-12 20:47 #8079607
-rw-r--r--   1 root root        3190 2006-05-06 19:43 #8079608
drwxr-xr-x   3 root root        4096 2007-03-10 13:24 #8552449
drwxr-xr-x   2 1000    1000     4096 2007-03-20 14:06 #8585255
drwxr-xr-x   2 1000    1000     4096 2007-03-13 23:38 #8601697
drwxr-xr-x   2 1000    1000     4096 2007-03-13 23:38 #8601698
-rw-r--r--   1 1000    1000    28391 2007-04-18 03:17 #8601716
-rw-r--r--   1 1000    1000    18619 2006-12-27 12:07 #8619489
-r--------   1 1000    1000       82 2006-12-26 02:08 #8619490
-rw-r--r--   1 1000    1000     5464 2006-12-26 02:08 #8619491
-rw-r--r--   1 1000    1000     1020 2006-11-27 11:48 #8619492
-rw-r--r--   1 1000    1000     9987 2006-12-25 18:43 #8619493
-rw-r--r--   1 1000    1000     4050 2006-12-25 18:43 #8619494
-rw-r--r--   1 1000    1000     1664 2007-02-02 12:37 #8619495
-r--------   1 1000    1000      178 2007-02-03 21:55 #8619496
-rw-r--r--   1 1000    1000     6149 2007-02-03 21:55 #8619497
-rw-r--r--   1 1000    1000     1129 2006-08-10 18:08 #8619498
-r--------   1 1000    1000      179 2007-01-09 03:12 #8619499
-rw-r--r--   1 1000    1000    16269 2007-01-09 03:12 #8619500
-rw-r--r--   1 1000    1000     1214 2006-11-27 11:48 #8619501
-rw-r--r--   1 1000    1000     1571 2006-12-27 12:07 #8619502
-r--------   1 1000    1000       82 2006-12-26 02:08 #8619503
-rw-r--r--   1 1000    1000     9524 2006-12-26 02:08 #8619504
-rw-r--r--   1 1000    1000      159 2006-08-10 18:08 #8619505
-rw-r--r--   1 1000    1000      158 2006-08-10 18:08 #8619506
-rw-r--r--   1 1000    1000     1541 2006-08-10 18:08 #8619507
-rw-r--r--   1 1000    1000      904 2007-01-09 03:23 #8619508
drwxr-xr-x   2 1000    1000     4096 2007-02-01 18:14 #8880545
-rw-r--r--   1 1000    1000       22 2007-02-01 18:14 #8880549
-rw-r--r--   1 1000    1000    23942 2007-02-01 18:14 #8880550
drwx------   2 1000    1000     4096 2007-04-12 03:07 #9027618
-rw-------   1 1000    1000      667 2007-04-12 03:15 #9027619
-rw-------   1 1000    1000   246528 2007-04-18 04:42 #9027668
-rw-------   1 1000    1000   589824 2007-04-18 04:42 #9027670
-rw-------   1 1000    1000   314165 2007-04-18 02:42 #9027681
-rw-------   1 1000    1000   321466 2007-04-18 02:42 #9027682
-rw-------   1 1000    1000   127669 2007-04-18 02:42 #9027683
-rw-------   1 1000    1000    40249 2007-04-18 02:42 #9027684
-rw-------   1 1000    1000    65617 2007-04-18 02:42 #9027685
-rw-------   1 1000    1000    29604 2007-04-18 02:42 #9027686
-rw-------   1 1000    1000    18818 2007-04-18 02:53 #9027687
-rw-------   1 1000    1000    27125 2007-04-18 02:53 #9027688
-rw-------   1 1000    1000    17022 2007-04-18 02:53 #9027689
-rw-------   1 1000    1000    44616 2007-04-18 02:53 #9027690
-rw-------   1 1000    1000   161524 2007-04-18 02:54 #9027691
-rw-------   1 1000    1000    47781 2007-04-18 02:54 #9027692
-rw-------   1 1000    1000    19607 2007-04-18 02:54 #9027693
-rw-------   1 1000    1000   444231 2007-04-18 02:58 #9027694
-rw-------   1 1000    1000    18148 2007-04-18 03:00 #9027695
-rw-------   1 1000    1000   120245 2007-04-18 03:00 #9027696
-rw-------   1 1000    1000   203522 2007-04-18 03:01 #9027697
-rw-------   1 1000    1000   123504 2007-04-18 03:03 #9027698
-rw-------   1 1000    1000   123226 2007-04-18 03:28 #9027705
-rw-------   1 1000    1000    41247 2007-04-18 03:28 #9027706
-rw-------   1 1000    1000    38211 2007-04-18 03:28 #9027707
-rw-------   1 1000    1000    78990 2007-04-18 03:28 #9027708
-rw-------   1 1000    1000    25214 2007-04-18 03:28 #9027709
-rw-------   1 1000    1000   139137 2007-04-18 04:26 #9027710
drwxr-xr-x   3 root root        4096 2007-04-18 04:37 #983041
drwxrwxrwt   2 root root        4096 2006-05-22 14:00 #9879554
drwxr-xr-x   9 root root        4096 2006-08-05 23:25 #9879555
drwxr-xr-x   2 root root        4096 2007-04-17 14:10 #9879556
drwxr-xr-x  10 root root        4096 2007-03-10 13:33 #9879557
drwxr-xr-x   2 root root        4096 2006-08-05 23:32 #9879558
drwxr-xr-x  24 root root        4096 2007-04-18 04:37 #9879559
drwxrwsr-x   2 root staff       4096 2006-05-22 14:00 #9879560
drwxr-xr-x   6 root root        4096 2007-04-18 04:37 #9879561
drwxrwsr-x   2 root mail        4096 2006-08-05 23:19 #9879562
drwxr-xr-x   2 root root        4096 2006-08-05 23:19 #9879563
drwxr-xr-x   6 root root        4096 2006-08-05 23:22 #9879564
drwxrwxrwt   2 root root        4096 2007-04-13 05:40 #9879565
-rw-r--r--   1 root root        1636 2007-04-15 15:32 #9879583
-rw-------   1 root root        4096 2007-04-18 02:40 #9879747
-rw-r--r--   1 root root         191 2007-04-17 00:09 #9879750
-rw-r--r--   1 root root    12905245 2006-06-08 15:06 #9879754
lrwxrwxrwx   1 root root          65 2007-03-10 13:23 #9880033 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansCondensed-Bold.ttf
lrwxrwxrwx   1 root root          72 2007-03-10 13:23 #9880034 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansCondensed-BoldOblique.ttf
lrwxrwxrwx   1 root root          68 2007-03-10 13:23 #9880035 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansCondensed-Oblique.ttf
lrwxrwxrwx   1 root root          60 2007-03-10 13:23 #9880036 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansCondensed.ttf
lrwxrwxrwx   1 root root          60 2007-03-10 13:23 #9880037 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
lrwxrwxrwx   1 root root          67 2007-03-10 13:23 #9880038 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansMono-BoldOblique.ttf
lrwxrwxrwx   1 root root          63 2007-03-10 13:23 #9880039 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansMono-Oblique.ttf
lrwxrwxrwx   1 root root          55 2007-03-10 13:23 #9880040 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSansMono.ttf
lrwxrwxrwx   1 root root          57 2007-03-10 13:23 #9880041 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
lrwxrwxrwx   1 root root          64 2007-03-10 13:23 #9880042 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerif-BoldOblique.ttf
lrwxrwxrwx   1 root root          60 2007-03-10 13:23 #9880043 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerif-Oblique.ttf
lrwxrwxrwx   1 root root          52 2007-03-10 13:23 #9880044 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerif.ttf
lrwxrwxrwx   1 root root          66 2007-03-10 13:23 #9880045 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerifCondensed-Bold.ttf
lrwxrwxrwx   1 root root          73 2007-03-10 13:23 #9880046 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerifCondensed-BoldOblique.ttf
lrwxrwxrwx   1 root root          69 2007-03-10 13:23 #9880047 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerifCondensed-Oblique.ttf
lrwxrwxrwx   1 root root          61 2007-03-10 13:23 #9880048 -> /usr/share/fon ts/truetype/ttf-dejavu/DejaVuSerifCondensed.ttf
-rw-r--r--   1 root root       18748 2006-08-05 23:31 #9880049
-rw-r--r--   1 root root        2950 2006-08-05 23:31 #9880050
lrwxrwxrwx   1 root root          47 2007-03-10 13:23 #9880051 -> /usr/share/fon ts/truetype/freefont/FreeMono.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880052 -> /usr/share/fon ts/truetype/freefont/FreeMonoBold.ttf
lrwxrwxrwx   1 root root          58 2007-03-10 13:23 #9880053 -> /usr/share/fon ts/truetype/freefont/FreeMonoBoldOblique.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880054 -> /usr/share/fon ts/truetype/freefont/FreeMonoOblique.ttf
lrwxrwxrwx   1 root root          47 2007-03-10 13:23 #9880055 -> /usr/share/fon ts/truetype/freefont/FreeSans.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880056 -> /usr/share/fon ts/truetype/freefont/FreeSansBold.ttf
lrwxrwxrwx   1 root root          58 2007-03-10 13:23 #9880057 -> /usr/share/fon ts/truetype/freefont/FreeSansBoldOblique.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880058 -> /usr/share/fon ts/truetype/freefont/FreeSansOblique.ttf
lrwxrwxrwx   1 root root          48 2007-03-10 13:23 #9880059 -> /usr/share/fon ts/truetype/freefont/FreeSerif.ttf
lrwxrwxrwx   1 root root          52 2007-03-10 13:23 #9880060 -> /usr/share/fon ts/truetype/freefont/FreeSerifBold.ttf
lrwxrwxrwx   1 root root          58 2007-03-10 13:23 #9880061 -> /usr/share/fon ts/truetype/freefont/FreeSerifBoldItalic.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880062 -> /usr/share/fon ts/truetype/freefont/FreeSerifItalic.ttf
lrwxrwxrwx   1 root root          60 2007-03-10 13:23 #9880063 -> /usr/share/fon ts/truetype/ttf-devanagari-fonts/Gargi_1.7.ttf
lrwxrwxrwx   1 root root          46 2007-03-10 13:23 #9880064 -> /usr/share/fon ts/truetype/thai/Garuda-Bold.ttf
lrwxrwxrwx   1 root root          53 2007-03-10 13:23 #9880161 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Ostorah.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880162 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Ouhod.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880163 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Petra.ttf
lrwxrwxrwx   1 root root          58 2007-03-10 13:23 #9880164 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Rasheeq_bold.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880165 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Rehan.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880166 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Salem.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880167 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Shado.ttf
lrwxrwxrwx   1 root root          53 2007-03-10 13:23 #9880168 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Sharjah.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880169 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Sindibad.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880170 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Tarablus.ttf
lrwxrwxrwx   1 root root          53 2007-03-10 13:23 #9880171 -> /usr/share/fon ts/truetype/ttf-arabeyes/ae_Tholoth.ttf
lrwxrwxrwx   1 root root          51 2007-03-10 13:23 #9880172 -> /usr/share/fon ts/truetype/ttf-bengali-fonts/ani.ttf
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880173 -> /usr/share/fon ts/type1/gsfonts/b018012l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880174 -> /usr/share/fon ts/type1/gsfonts/b018015l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880175 -> /usr/share/fon ts/type1/gsfonts/b018032l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880176 -> /usr/share/fon ts/type1/gsfonts/b018035l.pfb
lrwxrwxrwx   1 root root          44 2007-03-10 13:23 #9880177 -> /usr/share/fon ts/truetype/baekmuk/batang.ttf
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880178 -> /usr/share/fon ts/type1/gsfonts/c059013l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880179 -> /usr/share/fon ts/type1/gsfonts/c059016l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880180 -> /usr/share/fon ts/type1/gsfonts/c059033l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880181 -> /usr/share/fon ts/type1/gsfonts/c059036l.pfb
lrwxrwxrwx   1 root root          61 2007-03-10 13:23 #9880182 -> /usr/share/fon ts/truetype/ttf-devanagari-fonts/chandas1-1.ttf
-rw-r--r--   1 root root        1081 2006-08-05 23:31 #9880183
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880184 -> /usr/share/fon ts/type1/gsfonts/d050000l.pfb
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880185 -> /usr/share/fon ts/truetype/baekmuk/dotum.ttf
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880186 -> /usr/share/fon ts/truetype/baekmuk/gulim.ttf
lrwxrwxrwx   1 root root          43 2007-03-10 13:23 #9880187 -> /usr/share/fon ts/truetype/baekmuk/hline.ttf
lrwxrwxrwx   1 root root          59 2007-03-10 13:23 #9880188 -> /usr/share/fon ts/truetype/ttf-devanagari-fonts/kalimati.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880189 -> /usr/share/fon ts/truetype/kochi/kochi-gothic-subst.ttf
lrwxrwxrwx   1 root root          54 2007-03-10 13:23 #9880190 -> /usr/share/fon ts/truetype/kochi/kochi-mincho-subst.ttf
lrwxrwxrwx   1 root root          56 2007-03-10 13:23 #9880191 -> /usr/share/fon ts/truetype/ttf-bengali-fonts/lohit_bn.ttf
lrwxrwxrwx   1 root root          57 2007-03-10 13:23 #9880192 -> /usr/share/fon ts/truetype/ttf-gujarati-fonts/lohit_gu.ttf
-rw-r--r--   1 root root        8482 2006-08-05 23:31 #9880226
-rw-r--r--   1 root root       13244 2006-08-05 23:31 #9880227
-rw-r--r--   1 root root        2662 2006-08-05 23:31 #9880228
-rw-r--r--   1 root root        6026 2006-08-05 23:31 #9880229
-rw-r--r--   1 root root       19366 2006-08-05 23:31 #9880230
-rw-r--r--   1 root root        2468 2006-08-05 23:31 #9880231
-rw-r--r--   1 root root        4482 2006-08-05 23:31 #9880232
-rw-r--r--   1 root root       20624 2006-08-05 23:31 #9880233
-rw-r--r--   1 root root        4442 2006-08-05 23:31 #9880234
-rw-r--r--   1 root root       36409 2006-08-05 23:31 #9880235
-rw-r--r--   1 root root        3370 2006-08-05 23:23 #9880236
-rw-r--r--   1 root root       20364 2006-08-05 23:26 #9880237
-rw-r--r--   1 root root        2935 2006-08-05 23:28 #9880238
-rw-r--r--   1 root root        8701 2006-08-05 23:26 #9880239
-rw-r--r--   1 root root       23646 2006-08-05 23:31 #9880240
drwxr-xr-x   4 root root        4096 2006-08-05 23:23 #9880241
-rw-r--r--   1 root root      248661 2006-08-05 23:31 #9880242
-rw-r--r--   1 root root       63192 2006-08-05 23:31 #9880243
-rw-r--r--   1 root root        1296 2007-04-17 22:06 #9880983
-rw-r--r--   1 root root      412646 2007-03-30 13:29 #9881029
-rw-r--r--   1 root root        6035 2007-04-17 21:03 #9881068
-rw-r--r--   1 root root        6298 2007-03-01 12:05 #9881079
-rw-r--r--   1 root root        8687 2007-03-01 10:42 #9881083
-rw-r--r--   1 root root        1124 2007-03-23 02:47 #9881086
-rw-r--r--   1 root root         191 2007-04-17 22:06 #9881184
-rw-r--r--   1 root root         189 2007-03-23 02:47 #9881240
-rw-r-----   1 root slocate  1666472 2007-04-17 14:10 #9881488
-rw-r--r--   1 root root     1534216 2006-06-07 23:25 #9881697
-rw-r--r--   1 root root        2019 2007-03-23 02:47 #9881698
-rw-r--r--   1 root root        3153 2007-04-17 00:03 #9881773
-rw-r--r--   1 root root       86305 2007-04-17 00:03 #9881809
-rw-r--r--   1 root root         189 2007-04-17 20:39 #9881819
-rw-r--r--   1 root root       11041 2007-04-16 21:03 #9881841
-rw-r--r--   1 root root        4886 2007-04-17 22:33 #9881855
-rw-r--r--   1 root root         745 2007-04-17 22:06 #9881857
-rw-r--r--   1 root root        7232 2007-04-17 20:39 #9881858
-rw-r--r--   1 root root        3878 2007-04-17 22:06 #9881861
-rw-r--r--   1 root root        2062 2007-03-21 13:11 #9882366
-rw-r--r--   1 root root        4533 2007-03-21 13:10 #9882369
-rw-r--r--   1 root root        3036 2007-03-26 20:25 #9882370
-rw-r--r--   1 root root       23034 2006-06-29 22:26 #9882869
-rw-r--r--   1 root root       34750 2006-05-31 19:02 #9882981
-rw-r--r--   1 root root      471417 2006-06-20 08:25 #9883026
-rw-r--r--   1 root root     4343088 2006-06-08 12:23 #9883130
-rw-r--r--   1 root root     4784355 2006-06-11 01:17 #9883836
-rw-r--r--   1 root root      365627 2006-01-30 10:10 #9885214
-rw-r--r--   1 root root      152895 2006-01-30 10:10 #9885215
-rw-r--r--   1 root root        2388 2006-08-05 23:26 #9885216
-rw-r--r--   1 root root         268 2006-08-05 23:25 #9885219
-rw-r--r--   1 root root         212 2006-08-05 23:25 #9885220
-rw-r--r--   1 root root         152 2006-08-05 23:25 #9885221
-rw-r--r--   1 root root         101 2006-08-05 23:25 #9885222
-rw-r--r--   1 root root          52 2006-08-05 23:25 #9885223
-rw-r--r--   1 root root          36 2006-08-05 23:23 #9885226
-rw-r--r--   1 root root          13 2006-08-05 23:23 #9885227
-rw-r--r--   1 root root          59 2006-08-05 23:20 #9885228
-rw-r--r--   1 root root          11 2006-08-05 23:20 #9885229
-rw-r--r--   1 root root          53 2006-08-05 23:23 #9885230
-rw-r--r--   1 root root          13 2006-08-05 23:23 #9885231
-rw-r--r--   1 root root        3105 2007-03-28 14:21 #9885232
-rw-r--r--   1 root root        9172 2006-08-05 23:26 #9885233
-rw-r--r--   1 root root         157 2006-08-05 23:26 #9885235
-rw-r--r--   1 root root        1150 2006-08-05 23:26 #9885236
-rw-r--r--   1 root root         304 2006-08-05 23:26 #9885237
-rw-r--r--   1 root root         152 2007-03-28 14:21 #9885377
-rw-r--r--   1 root root      707456 2007-04-16 02:47 #9895943
-rw-------   1 root root       75377 2007-04-18 04:43 #9912324
drwxr-xr-x   2 root root        4096 2006-08-05 23:33 #9912353
drwxr-xr-x   2 root root        4096 2006-08-05 23:33 #9912355
d---------   2 root root        4096 2007-03-10 13:36 #9912357
drwxr-xr-x   2 root root        4096 2006-08-05 23:25 #9913267
drwxr-xr-x   2 root root        4096 2007-03-11 18:06 #9913269
-rw-r--r--   1 root root          18 2007-03-10 13:24 #9913293
d---------   2 root root        4096 2007-03-10 13:36 #9913294
d---------   2 root root        4096 2007-03-10 13:38 #9913296
d---------   3 root root        4096 2007-03-10 13:40 #9913299
-rw-r--r--   1 root root         246 2007-01-29 14:27 #9913317
-rw-r--r--   1 root root          18 2007-01-29 14:37 #9913323
-rw-r--r--   1 root root          12 2007-01-29 14:27 #9913328
-rw-r--r--   1 root root          18 2007-01-29 14:40 #9913329
-rw-r--r--   1 root root         318 2007-01-29 14:35 #9913330
-rw-r--r--   1 root root          18 2007-01-29 14:29 #9913331
-rw-r--r--   1 root root          44 2007-01-29 14:22 #9913332
-rw-r--r--   1 root root          18 2007-01-29 14:34 #9913333
-rw-r--r--   1 root root          24 2007-01-29 14:36 #9913334
-rw-r--r--   1 root root          18 2007-01-29 14:36 #9913335
-rw-r--r--   1 root root          18 2007-01-29 14:33 #9913336
-rw-r--r--   1 root root          99 2007-01-29 14:19 #9913337
-rw-r--r--   1 root root          18 2007-01-29 14:27 #9913339
-rw-r--r--   1 root root          18 2007-01-29 14:36 #9913340
-rw-r--r--   1 root root          18 2007-01-29 14:11 #9913341
-rw-r--r--   1 root root          90 2007-01-29 14:07 #9913342
-rw-r--r--   1 root root          36 2007-01-29 14:18 #9913343
-rw-r--r--   1 root root          18 2007-01-29 14:18 #9913344
-rw-r--r--   1 root root         360 2007-01-29 14:16 #9913345
-rw-r--r--   1 root root          18 2007-01-29 14:20 #9913346
-rw-r--r--   1 root root          36 2007-01-29 14:28 #9913347
-rw-r--r--   1 root root          12 2007-01-29 14:32 #9913348
-rw-r--r--   1 root root          90 2007-01-29 14:02 #9913349
-rw-r--r--   1 root root          12 2007-01-29 14:34 #9913350
-rw-r--r--   1 root root          18 2007-01-29 14:15 #9913351
-rw-r--r--   1 root root          36 2007-01-29 14:02 #9913352
-rw-r--r--   1 root root          36 2007-01-29 14:03 #9913353
-rw-r--r--   1 root root          36 2007-01-29 14:01 #9913354
-rw-r--r--   1 root root          18 2007-01-29 14:36 #9913355
-rw-r--r--   1 root root          72 2007-01-29 14:15 #9913356
-rw-r--r--   1 1000    1000    58956 2007-04-10 01:34 #9945411
-rw-r--r--   1 1000    1000     7431 2007-04-10 01:34 #9945412
d---------   6 root root        4096 2007-04-18 04:30 #9961473
d---------   3 root root        4096 2007-03-22 05:57 #9961562
-rw-r--r--   1 root root        4156 2007-04-16 02:54 #9977874
-rw-r--r--   1 root root         296 2007-04-16 02:54 #9977875
-rw-r--r--   1 root root       65749 2007-04-16 02:54 #9977876


```

---

### Post by freebird54 on 2007-04-19
Essentially what it means is that nothing much useful remains on that partition.  I don't think there is anything useful to be done at this point - unless you want to look through what is there, and try to copy off anything you need to somehere else.  All the entries without names are the equivalnet of 'lost clusters'  They are parts of files, and the system didn't know what the files were.

If you go through that long list, and recognize something you need, it can be rescued.  use 

```
ls -la | less
```

to page through it if you want. 

How depressing.  Was there much there that you created/added/don't have backups for?

---

### Post by freebird54 on 2007-04-19
Unfortunately I have to go and locate a CPU fan for my sister.  I'll be a while before I can answer anymore posts....(sigh)

you could start a new thread with 'What now - lost root partition' as a topic I guess - but there'll be HEAVY traffic on here with Feisty just out.

Good luck - and TTYL

---

### Post by yamswirl on 2007-04-19
Mostly just some pictures of family and kittys, my apartment so my landlord doesn't try to say I ruined anything.  :sad: I just wanted to be able to get the couples pictures of my grandma.  sigh.

So at this point if I reinstall from the cd will that start me over from the very beginning?  And I JUST got dvds to play last week.  Man...

---

### Post by freebird54 on 2007-04-19
Sounds like it might be worth the time to page through the listing using that ls | less command, and see if any of those pix remain.  Maybe use the opportunity to get upgraded to Feisty?  Should be easier to get the DVD going that way, at least.

Sorry it didn't turn out too well...

---

### Post by yamswirl on 2007-04-19
Do you have the time to help me out with this a bit more? [-o<  As far as trying to back up anything that might be there and upgrading.  Thanks for all the time you've taken to get to this point. :grin:  You've been FAR more helpful than out tech guy at work.  All he said was, "Grub error 15.  That's bad." 

Did you find a fan?

---

### Post by freebird54 on 2007-04-19
Yup - to both I guess.  As soon as I arrived with the fan, of course I am getting agitation to get it installed!  Hmm - let's see - if I lean on this corner, will it hook up? or crack the processor wide open?... :D

As for finding the files to backup - I might try this:

ls -la lost+found > filelist.txt

This will create filelist.txt, which you can then put in a text editor (gedit) or something like AbiWord.  Start at the top corner, hold the shift key, and <down> arrow till you see something interesting.  Stop the highlighting just above such interesting object, and hit <del>.  move past interesting object, and hold shift again - till just before the next interesting object. <del> again. Repeat until only interesting things are left.

Depending on the number of interesting things is the next thing to do... :)

---

### Post by yamswirl on 2007-04-19
grumble, grumble...

now it's saying no such file or directory.  

So at some point I was thinking and backed up some picts on the external (before I ditched Windows on my laptop).  So I didn't lose absolutly everything.  

So I'm thinking.  Maybe at this point it would be a better idea just to follow the herd and upgrage or change to Feisty.  Do fawns travel in herds?

In theory I can just click on the download by the huge announcemt and follow instructions.  Right.

It's probably best not to break the CPU.  ;) That's my understanding anyway.

---

### Post by freebird54 on 2007-04-19
I am quite sure that's the way my sis thinks...

Only you know what's lost, and what might be found.  But following the herd is something that mama doe does, and the fawns knows better than  to wander - no matter how Feisty!

How big *IS* the file that command generates?  Remember, you should in /mnt/ubuntu when you give it... (that's the root of what's left of that partition..)

---

### Post by yamswirl on 2007-04-19
So when I run ls -la | less I get
```
total 104
drwxr-xr-x   3 root root  4096 2007-03-22 02:51 .
drwxr-xr-x   5 root root    60 2007-04-19 18:41 ..
drwxr-xr-x 424 root root 98304 2007-03-10 13:16 lost+found

```

I can't seem to move anywhere in there though.  Somehow it seems to be getting less and less important.

---

### Post by yamswirl on 2007-04-19
Now, if I upgrade to Feisty like all the other kids will that take care of the awfulness that I have caused on my computer?

Hmm.  Looks like I'll have to download, not upgrade since I'm not using Edgy.  That doesn't really change the question though.

---

### Post by freebird54 on 2007-04-19
Yup - might as well.  And if you have access to a torrent, it should be much faster that way.

BTW  the full command was 
```

ls -la lost+found | less > filetext.txt
```

but as you have a fair bit of it - go ahead wth the Plan B (or Plan F I guess :)

Enjoy = the fawn is a nice one!

---

### Post by yamswirl on 2007-04-19
I tried the full command.  It didn't do what it was supposed to.  File not found or something.  Oh well.

So was that a "Yup" as far as installing Fawn will get rid of my evil grub error?  I don't have any blank disks right now so I've sent along instructions to my bf to take care of that for me tomorrow,  So hopefully tomorrow night I'll be able to install that and be a happy camper.

Even though this didn't end all happy the way I'd like, thanks a lot for all the help.  You rock!  If you need any librarian help just let me know.  Ya know, fact finding, document finding, trivia finding...  I can find the info, I just don't always know how to use it.  ;)

---

### Post by freebird54 on 2007-04-19
Yup should take of the rest of the problems (at least of the computer variety).  Sorry we couldn't come up with a better fix - but I suspect that you inadvertantly tried to apply a change to the main (root) partition rather than your target (whatever it was).

I think nearly everyone has to that once (lose their stuff) before they understand that all stuff about backups actually has meaning rather than just being background noise (yeah, yeah, I know). Even if all you save that way is a data directory, that's the stuff you create yourself :)

Enjoy the Fawn!  (and the explanation to the BF)  :guitar: 

BCNUL8R

---

### Post by yamswirl on 2007-04-19
You'll see me when I'm trying to partition my external hard drive again. I got it to back up my files. :lol:  Ahhh.  Funny that.

---

