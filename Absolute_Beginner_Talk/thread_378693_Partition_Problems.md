---
title: "Partition Problems"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by BigBabyDaddy1968 on 2007-03-07
I posted earlier about a problem I had with the automatic partitioner in that it crashed XP and I had to reinstall a fresh version.  As a result of that less-than-pleasant experience, I decided to manually create the partitions.  However, for some reason, I ended up with...well, you tell me, if ya can.... :D 

When I reinstalled XP, I created a partition for it (C: ) of roughly half the HD and formatted it to ntfs.  The clean, fresh version of XP for Media Center edition went there and is just fine.  I left the rest of the HD as RAW, intending Ubuntu to go there, and format to ext3.   But when I tried to do the root, swap, and home partitions, the operations failed, giving me a mess.  I have:

*  /dev/sda1     ntsf             107.42gb (for windows)
*  /dev/sda2     extended     125.39
        -- /dev/sda5   unknown   125.39
*  /dev/sda3     unknown   7.84
*   unallocated  unallocated   7.84  

Right clicking the unkowns gets an error message.

I'm just trying to go with 12gb for root, 1gb for swap, and the 125-ish gb for home, using the unformatted partition to do so.  Do I need to create partitions of those sizes in windows setup, so I have the C: for windows (ntsf), then D: of 125-ish gb left as RAW to be formatted for home thru Ubuntu install, an E: 1 gb for swap, then F: of 12gb for the root?  Am I missing something else?

And I am feeling quite stupid, having borked XP and being unable to get past the partitions even though I've read psychocats excellent guide.  The computer is a very new Dell XPS 410 w/ an Intel dual core processor, so it's not like the equipment can't handle it.  It's clearly user error, but I'm stumped.... I'm not even entirely sure I'm making sense now.... ](*,) 

Thanks,
BBD

---

### Post by AtrejuT on 2007-03-07
What programme are you actually using to make the partitions?
If you are booting a live cd you should be able to start gparted. There you can just remove all the partitions you don't want and add new ones. Don't forget to format them to whatever you want and you should be ready to go.

atreju

---

### Post by BigBabyDaddy1968 on 2007-03-07
I am using gparted, but when I right click and go into that screen, it won't let me choose between primary, extended, or logical.  I can format to ext3 it seems, but the operations fail, even though it did just fine for the sda2.

As I understand, it, I should not create E:, F:, and more partitons through windows, just do so from gparted?

---

### Post by AtrejuT on 2007-03-07
sorry, I might be stupid here, but that means it doesn't even let you delete the partitions you have? (You want to keep sda1 obviously, but I'm talking about the others). Rather unlikely, but might they be mounted somewhere by any chance? Thats the only case I ever experienced of not being able to edit my partitions in gparted.

You don't really need an extended partition I think, since you want to have four partitions which is just what you can have without using an extended partition. But I understand you don't ever get far enough to be able to change that.
atreju

---

### Post by BigBabyDaddy1968 on 2007-03-07
So I don't need to worry about whether or not a particular partition is primary, logical, or extended as long as they're all (root, home, and swap) ext3 (or whatever I choose)?  Maybe I should just try again...?  The partitions didn't mount, so I never got past step 5 of the 6....

Again, thanks for your help and patience  on what must surely be a relatively panicky post from an obvious n00b.

---

### Post by bodhi.zazen on 2007-03-07
I do not know why you are having problems with your partitions.

I would advise you try, in order, 

1.  The gparted live cd. The version of gparted on the live CD is more up to date then the Ubuntu live CD ...

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)



2. cfdisk

In the past, with previous versions of gparted, the partitions would get re-numbered or problematic.

Use cfdisk to re-partition, and then if you need you can resize with gparted ...

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

EDIT:

Basic partitioning : [http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

---

### Post by AtrejuT on 2007-03-07
ok, sorry, I had been gone for a while:
You can have a maximum of four primary partitions on your harddisk. If you want more you need to use an extended partition (which is not really a partition yet, but just something to keep logical partitions in) and several logical partitions in the extended one. But you don't want that I think.

Since you only need four partitions (windows, /, swap, /home) you can just use four primary partitions.  (That's what I do actually) These do not need to use the same Filesystem. In fact, Windows should use NTFS, swap must use swap and the other two can be pretty much whatever you want - I'd recommend ext3 as you already said yourself.

So I'd recommend deleting all partitions but sda1 and then making three new primary partitions of the size you want. Format two of them to ext3 for / and /home, and one of them to swap.

atreju

---

### Post by BigBabyDaddy1968 on 2007-03-07
OK, I was able to delete the mess I made before and have /dev/sda1 NTFS (for XP). and one unallocated, unformatted partition of 125.41 gb...which I shall now try to split as I described above. Thanks again!

BTW, bhodi, thanks for those links.  Your guide thread was particularly useful.

Here goes...hopefully something.... :)

---

### Post by BigBabyDaddy1968 on 2007-03-07
Sorry to bump...but not sorry enough to not do it. ;)

It seems the installation went OK, and I was able to repartition as described above.  Now, however, I can't seem to boot ubuntu from anywhere but the live cd.... :confused: 

Does this mean I've buggered the mounting?  The computer shows the ntfs formatted HD as being the size I allocated, but then nothing else (which is normal as I understand XP doesn't really see anything when done like this)....

Feel free to smack-a-n00b....

---

### Post by mikewhatever on 2007-03-07
In Ubuntu, can you open the terminal (Applications->Accessories->Terminal) and type and post the output of the following:
> 
sudo fdisk -l
sudo gedit /boot/grub/menu.lst

Do you get any errors while trying to boot Ubuntu?

---

### Post by BigBabyDaddy1968 on 2007-03-07
> **mikewhatever said:**
> Do you get any errors while trying to boot Ubuntu?
It says
> sudo: /boot/grub/menu.: command not found
bash: st: command not found

Also, is tha "|" or a lower case L...?  I tried both ways and got that same response....

---

### Post by BigBabyDaddy1968 on 2007-03-07
OK, I think I have what I need in the "Prepare mount points" part of the install.  Partition 1/SATA1 is the windows partition (ntfs), then there's partitions 1 (SATA 2), 2, 3, & 4, which are the ones I've set up for root, swap, and home.  

Does it look like I need to reformat?  Or just hit forward and go?

Again, I cannot tell you all how much I appreciate any guidance.

---

### Post by kevmartin on 2007-03-07
> **BigBabyDaddy1968 said:**
> It says


Also, is tha "|" or a lower case L...?  I tried both ways and got that same response....

It's a lower case L in both commands :-)

Looks from your screen shot like you you used the | (pipe character)  in the fdisk commands which upset everything in the following line

---

### Post by BigBabyDaddy1968 on 2007-03-07
OK, got that part....no grub installed....

Here's the "prepare partitions" screen.  My intention was 12gb root ext3, a bit over 1gb for swap (linux-swap?), and the balance as ext3 as well.

---

### Post by bodhi.zazen on 2007-03-08
Looks good ....

---

### Post by BigBabyDaddy1968 on 2007-03-13
Still having problems.  I created the partitions as I described, but when I click forward to the mount points, and it looks like it just does what the hell it wants.

Another screen shot?  I think yes! I made what I think are corrections, which now show up in the install screen.

---

### Post by Sweet Spot on 2007-03-13
Guys, I've been walking BBD through the partitioning via IM, and it seems that things have gotten to the point of where it should reboot after the install was finished and then go back to finish the install, but grub doesn't load. However, it's been a while since MY install, and I can't remember the whole install process. 

I'm about to actually back up all my stuff so that I can do the install again (which I'd rather not do but hey...) and go through it to see if perhaps there's a problem with the .ISO or if it's something else we're missing.   Here's a log of our conversation up until this pointL > [SIZE=3] It's a live CD![/SIZE]
[COLOR=#204a87][SIZE=2](07:03:50 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]awesomeness[/SIZE]
[SIZE=2][COLOR=#cc0000](07:03:53 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] However, supper beckons...BRB[/SIZE]
[COLOR=#204a87][SIZE=2](07:04:04 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]almost as awesome as the fresh mozzarella I'm munching on [/SIZE]
[SIZE=2][COLOR=#cc0000](07:04:06 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] I'm already @ the prepare partitions page[/SIZE]
[SIZE=2][COLOR=#cc0000](07:04:11 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :D[/SIZE]
[COLOR=#204a87][SIZE=2](07:04:14 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]great ![/SIZE]
[COLOR=#204a87][SIZE=2](07:04:22 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, go and eats, and we'll see you soon[/SIZE]
[COLOR=#204a87][SIZE=2](07:04:24 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]mangia[/SIZE]
[COLOR=#204a87][SIZE=2](07:13:54 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] [http://uploadpalace.com/en/download.php?id=5F6954A91](http://uploadpalace.com/en/download.php?id=5F6954A91)[/SIZE]
[SIZE=2][COLOR=#cc0000](07:56:27 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Okee-dokee[/SIZE]
[COLOR=#204a87][SIZE=2](07:57:41 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] so shall we try this without me doing anything first ?[/SIZE]
[COLOR=#204a87][SIZE=2](07:57:54 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]perhaps I'll just back my stuff up in case[/SIZE]
[SIZE=2][COLOR=#cc0000](07:57:55 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] I think yes...[/SIZE]
[SIZE=2][COLOR=#cc0000](07:58:08 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] back-up is always good anyway....[/SIZE]
[COLOR=#204a87][SIZE=2](07:58:20 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Lessie... move some porn from here to here... and then some porn from here to here....[/SIZE]
[SIZE=2][COLOR=#cc0000](07:59:04 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Heh[/SIZE]
[SIZE=2][COLOR=#cc0000](07:59:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] I'll just ask as I go along....[/SIZE]
[COLOR=#204a87][SIZE=2](07:59:24 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, you go ahead, and I'll start backing up[/SIZE]
[COLOR=#204a87][SIZE=2](07:59:34 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ooh... we likes projects prescious ![/SIZE]
[COLOR=#204a87][SIZE=2](08:00:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]oh ****. Just realized that I have to burn about 6 movies[/SIZE]
[COLOR=#204a87][SIZE=2](08:00:15 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]guess I'll start there[/SIZE]
[SIZE=2][COLOR=#cc0000](08:02:21 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] What's the dif betwen /dev/sda and /dev/sdb?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:02:50 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] I'm seeing that choice in the upper R drop-down menu[/SIZE]
[SIZE=2][COLOR=#cc0000](08:03:32 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] the sda shows my ntsf, linux-swap, and both ext3 partitions.[/SIZE]
[SIZE=2][COLOR=#cc0000](08:04:05 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] [ Audible [http://us.dl1.yimg.com/download.yahoo.com/dl/aud/in/base.in.gujarati.itsdone.swf](http://us.dl1.yimg.com/download.yahoo.com/dl/aud/in/base.in.gujarati.itsdone.swf) ] thaiii.....ghaiii...uuuuu[/SIZE]
[COLOR=#204a87][SIZE=2](08:04:06 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]right um.... [/SIZE]
[SIZE=2][COLOR=#cc0000](08:04:48 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] the sdb shows I have 2 partitions of an unknown filesystem[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:04 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]do you have another hd there ?[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:12 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]external or something ?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:05:17 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] nope[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:21 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so just one HD[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:28 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]weird[/SIZE]
[SIZE=2][COLOR=#cc0000](08:05:30 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] yup[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:45 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]did you just create those partitions ?[/SIZE]
[COLOR=#204a87][SIZE=2](08:05:51 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]prolly not. delete them[/SIZE]
[SIZE=2][COLOR=#cc0000](08:06:09 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] delete all but the ntfs, right?[/SIZE]
[COLOR=#204a87][SIZE=2](08:07:06 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]sec[/SIZE]
[SIZE=2][COLOR=#cc0000](08:07:31 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] nero is done[/SIZE]
[COLOR=#204a87][SIZE=2](08:08:34 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]well, I have: "dev/hda"  (my primary HD w/dual boot)[/SIZE]
[COLOR=#204a87][SIZE=2](08:08:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and then[/SIZE]
[SIZE=2][COLOR=#cc0000](08:08:39 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] but it wants a serial #[/SIZE]
[COLOR=#204a87][SIZE=2](08:08:51 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]dev/hdb[/SIZE]
[COLOR=#204a87][SIZE=2](08:09:00 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]which is my secondary 20 gig drive[/SIZE]
[COLOR=#204a87][SIZE=2](08:09:11 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Yeah, I gave you the key creator for that[/SIZE]
[COLOR=#204a87][SIZE=2](08:09:19 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]that was the small file I gave you[/SIZE]
[SIZE=2][COLOR=#cc0000](08:09:26 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Ohhhhhh...that's what that was....[/SIZE]
[SIZE=2][COLOR=#cc0000](08:09:34 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] On the other comp....[/SIZE]
[SIZE=2][COLOR=#cc0000](08:09:47 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] So delete all but the ntfs?[/SIZE]
[COLOR=#204a87][SIZE=2](08:09:53 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and interestingly enough...[/SIZE]
[SIZE=2][COLOR=#cc0000](08:09:59 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Then recreate the same partitions.....[/SIZE]
[COLOR=#204a87][SIZE=2](08:10:10 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]my external drive shows up as "dev/sda"[/SIZE]
[SIZE=2][COLOR=#cc0000](08:10:26 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] do u have dev/sdb?[/SIZE]
[COLOR=#204a87][SIZE=2](08:10:41 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]nope[/SIZE]
[COLOR=#204a87][SIZE=2](08:10:48 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]just hda and hdb[/SIZE]
[SIZE=2][COLOR=#cc0000](08:11:01 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Hmm...oh well.[/SIZE]
[COLOR=#204a87][SIZE=2](08:11:02 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]which Im assuming is HD "a"[/SIZE]
[COLOR=#204a87][SIZE=2](08:11:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and HD "b"[/SIZE]
[COLOR=#204a87][SIZE=2](08:11:13 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]but wtf do I know[/SIZE]
[COLOR=#204a87][SIZE=2](08:11:24 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yes delete all but ntfs[/SIZE]
[SIZE=2][COLOR=#cc0000](08:11:27 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] The HD supposedly has some sort og ghost backup, but i don't think that's causing it.[/SIZE]
[COLOR=#204a87][SIZE=2](08:11:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I hope not. because if it's doing something funky, I'd be pissed. [/SIZE]
[SIZE=2][COLOR=#cc0000](08:11:54 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i'm abandoning the caps on this comp...shift key is borked.[/SIZE]
[COLOR=#204a87][SIZE=2](08:12:15 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]can you perhaps check to see if that option is disable-able in the bios?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:12:23 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] what's really odd is the sda and sdb are the exact same size...232.83 gb[/SIZE]
[COLOR=#204a87][SIZE=2](08:12:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]impossible, since your HD isn't even that big[/SIZE]
[COLOR=#204a87][SIZE=2](08:12:50 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]right ?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:12:55 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] right.[/SIZE]
[SIZE=2][COLOR=#cc0000](08:13:03 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] goofy ****....[/SIZE]
[COLOR=#204a87][SIZE=2](08:13:05 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]get rid of the crap[/SIZE]
[SIZE=2](08:13:52 PM) [/SIZE]**[SIZE=3]Offering to send Screenshot.png to bigbabydaddy1968[/SIZE]**
[SIZE=2](08:13:55 PM) [/SIZE]**[SIZE=3]Transfer of file Screenshot.png complete[/SIZE]**
[COLOR=#204a87][SIZE=2](08:14:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]again, that's what my partitions look like[/SIZE]
[COLOR=#204a87][SIZE=2](08:14:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]you should have similar or the exact same results, more or less[/SIZE]
[SIZE=2][COLOR=#cc0000](08:15:06 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Hmm.[/SIZE]
[COLOR=#204a87][SIZE=2](08:15:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]it looks to me as if I created the ext 3 partitions as well as the swap in an extended partition[/SIZE]
[COLOR=#204a87][SIZE=2](08:16:02 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so when you delete those partitions you should have one empty space[/SIZE]
[SIZE=2][COLOR=#cc0000](08:16:12 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] right[/SIZE]
[COLOR=#204a87][SIZE=2](08:16:17 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]with it, try creating an extended partition[/SIZE]
[COLOR=#204a87][SIZE=2](08:16:53 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]then within that extended partition, create logical partitions, which I think ARE the swap and ext 3 ones[/SIZE]
[SIZE=2][COLOR=#cc0000](08:17:01 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] deleting[/SIZE]
[COLOR=#204a87][SIZE=2](08:17:12 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]lemmie burn movie[/SIZE]
[COLOR=#204a87][SIZE=2](08:17:13 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]s[/SIZE]
[SIZE=2][COLOR=#cc0000](08:17:44 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] now i have 107.42gb as sda1 (winblows C: drive)[/SIZE]
[COLOR=#204a87][SIZE=2](08:18:02 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]sounds right[/SIZE]
[SIZE=2][COLOR=#cc0000](08:18:02 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] and 125.41 gb of unallocated space[/SIZE]
[COLOR=#204a87][SIZE=2](08:18:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]sounds right too[/SIZE]
[SIZE=2][COLOR=#cc0000](08:18:30 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] right click, then "new"[/SIZE]
[COLOR=#204a87][SIZE=2](08:18:39 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]sounds about right, I think[/SIZE]
[COLOR=#204a87][SIZE=2](08:18:45 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]don't remember though[/SIZE]
[SIZE=2][COLOR=#cc0000](08:18:47 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Primary partition?[/SIZE]
[COLOR=#204a87][SIZE=2](08:18:53 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]what other options are there[/SIZE]
[SIZE=2][COLOR=#cc0000](08:19:03 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] should that be home?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:19:08 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3]  does it matter?[/SIZE]
[COLOR=#204a87][SIZE=2](08:19:14 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]don't skip ahead that far yet[/SIZE]
[SIZE=2][COLOR=#cc0000](08:19:33 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] primary or extended[/SIZE]
[SIZE=2][COLOR=#cc0000](08:19:37 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] are the options[/SIZE]
[COLOR=#204a87][SIZE=2](08:20:12 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]try extended[/SIZE]
[COLOR=#204a87][SIZE=2](08:20:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]man, I haven't seen this movie in years... "The Last Dragon"[/SIZE]
[COLOR=#204a87][SIZE=2](08:21:02 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Bruce Leroy  etc..[/SIZE]
[SIZE=2][COLOR=#cc0000](08:21:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] making that my root of 12 gb[/SIZE]
[COLOR=#204a87][SIZE=2](08:21:29 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]wait... no...[/SIZE]
[SIZE=2][COLOR=#cc0000](08:21:33 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] ok[/SIZE]
[COLOR=#204a87][SIZE=2](08:24:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]damn burn is causing the partition manager to not read it[/SIZE]
[COLOR=#204a87][SIZE=2](08:24:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]it'll have to wait[/SIZE]
[SIZE=2][COLOR=#cc0000](08:24:21 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] mine? yours?[/SIZE]
[COLOR=#204a87][SIZE=2](08:24:22 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]but here's what I'm thinking[/SIZE]
[COLOR=#204a87][SIZE=2](08:24:23 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]mine[/SIZE]
[COLOR=#204a87][SIZE=2](08:25:36 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, if you look at my screen shot[/SIZE]
[SIZE=2][COLOR=#cc0000](08:25:47 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] yes[/SIZE]
[COLOR=#204a87][SIZE=2](08:26:04 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]NTFS is the 20 gig partition[/SIZE]
[SIZE=2][COLOR=#cc0000](08:26:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] your external hd?[/SIZE]
[COLOR=#204a87][SIZE=2](08:26:22 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]no, ... [/SIZE]
[COLOR=#204a87][SIZE=2](08:26:26 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]it's the primary HD[/SIZE]
[SIZE=2][COLOR=#cc0000](08:26:31 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] ok[/SIZE]
[COLOR=#204a87][SIZE=2](08:26:39 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]XP is sharing hd w/Ubuntu[/SIZE]
[COLOR=#204a87][SIZE=2](08:26:53 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, so then...[/SIZE]
[COLOR=#204a87][SIZE=2](08:27:47 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]extended hda2 is 133.13 gb and is the bulk of the HD, which in total is 160 gigs[/SIZE]
[SIZE=2][COLOR=#cc0000](08:28:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] k[/SIZE]
[COLOR=#204a87][SIZE=2](08:28:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]FROM the extended partition, I created I'm thinking... logical drives. The first of which looks to be ext3 which is root[/SIZE]
[COLOR=#204a87][SIZE=2](08:29:27 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]second partition looks to be just swap and the next partition (also logical I'm thinking) is home @ 120.41 gigs[/SIZE]
[COLOR=#204a87][SIZE=2](08:29:44 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5](or third partition i should say ?)\[/SIZE]
[COLOR=#204a87][SIZE=2](08:30:12 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Problem is, I forget whether or not swap needs a partition or if it's self contained[/SIZE]
[COLOR=#204a87][SIZE=2](08:30:31 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]it looks like it's IN the extended partition though, physically speaking[/SIZE]
[SIZE=2][COLOR=#cc0000](08:32:11 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] on psychocats, it looks like the extended partition is subdivideinto home, swap, and root.[/SIZE]
[COLOR=#204a87][SIZE=2](08:32:36 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]right, and I believe those subdivisions are logical[/SIZE]
[COLOR=#204a87][SIZE=2](08:33:09 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]but hey, don't take it from me, I'm only running a working version of ubuntu....:(|)[/SIZE]
[SIZE=2][COLOR=#cc0000](08:33:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] heh[/SIZE]
[SIZE=2][COLOR=#cc0000](08:33:37 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] [ Audible [http://us.dl1.yimg.com/download.yahoo.com/dl/aud/us/base.us.insults.snap_08.swf](http://us.dl1.yimg.com/download.yahoo.com/dl/aud/us/base.us.insults.snap_08.swf) ] Ohhhhhh snap![/SIZE]
[COLOR=#204a87][SIZE=2](08:34:59 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]lol[/SIZE]
[SIZE=2][COLOR=#cc0000](08:36:54 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] OK, now I have one big /dva/sda2 extended[/SIZE]
[COLOR=#204a87][SIZE=2](08:37:01 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]cool[/SIZE]
[COLOR=#204a87][SIZE=2](08:37:13 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I think[/SIZE]
[COLOR=#204a87][SIZE=2](08:37:28 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, now create a logical drive[/SIZE]
[SIZE=2][COLOR=#cc0000](08:37:30 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] when i go to subdivide, it only allows the logical partition option....[/SIZE]
[COLOR=#204a87][SIZE=2](08:37:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yeap[/SIZE]
[SIZE=2][COLOR=#cc0000](08:37:41 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] what size, though?[/SIZE]
[COLOR=#204a87][SIZE=2](08:37:56 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]first one should be root[/SIZE]
[SIZE=2][COLOR=#cc0000](08:38:01 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i was gonna go w/ 12gb for root....[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:06 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]then swap, then home[/SIZE]
[SIZE=2][COLOR=#cc0000](08:38:06 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] so  12 gb, then?[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:09 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yep[/SIZE]
[SIZE=2][COLOR=#cc0000](08:38:10 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] heh[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:32 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so you're creating 3 logical drives each from the extended partition[/SIZE]
[SIZE=2][COLOR=#cc0000](08:38:40 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] next screen: logical as well[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:41 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]or at least that's my theory[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:46 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yeah, swap[/SIZE]
[COLOR=#204a87][SIZE=2](08:38:59 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]gig should be enough[/SIZE]
[SIZE=2][COLOR=#cc0000](08:39:01 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] so we'll resize it to about 1.5gb for the linux-swap[/SIZE]
[COLOR=#204a87][SIZE=2](08:39:05 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok[/SIZE]
[COLOR=#204a87][SIZE=2](08:39:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]fair nuff[/SIZE]
[COLOR=#204a87][SIZE=2](08:39:53 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]after all are created, I guess you go to next page, and match up the partitons with the names/sizes of them[/SIZE]
[SIZE=2][COLOR=#cc0000](08:39:58 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] now i have about 114gb left for another logical partition....[/SIZE]
[COLOR=#204a87][SIZE=2](08:40:04 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]right, that's home[/SIZE]
[SIZE=2][COLOR=#cc0000](08:40:07 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] that will become home, eh?[/SIZE]
[COLOR=#204a87][SIZE=2](08:40:10 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]indeed[/SIZE]
[SIZE=2][COLOR=#cc0000](08:40:27 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] time to click forward[/SIZE]
[COLOR=#204a87][SIZE=2](08:40:39 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]march young soldier ![/SIZE]
[SIZE=2][COLOR=#cc0000](08:41:00 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] "applying pending operations"[/SIZE]
[COLOR=#204a87][SIZE=2](08:41:06 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yummy ![/SIZE]
[SIZE=2][COLOR=#cc0000](08:41:11 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] prepare mount points...[/SIZE]
[COLOR=#204a87][SIZE=2](08:41:17 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]go to it [/SIZE]
[SIZE=2][COLOR=#cc0000](08:41:18 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] been here before, gawdammit[/SIZE]
[SIZE=2][COLOR=#cc0000](08:41:20 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :D[/SIZE]
[COLOR=#204a87][SIZE=2](08:41:28 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]tackle that bad boy ![/SIZE]
[COLOR=#204a87][SIZE=2](08:41:37 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]round house em' ![/SIZE]
[SIZE=2][COLOR=#cc0000](08:41:51 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] wait a flippn minute[/SIZE]
[COLOR=#204a87][SIZE=2](08:41:58 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]rrrrr....Grrrr.r....[/SIZE]
[COLOR=#204a87][SIZE=2](08:42:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]WHAT[/SIZE]
[COLOR=#204a87][SIZE=2](08:42:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]make sure you're matching them up.[/SIZE]
[SIZE=2][COLOR=#cc0000](08:42:37 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] it's showing 3 partitions for mount points[/SIZE]
[COLOR=#204a87][SIZE=2](08:42:43 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and they are ?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:42:45 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] 2 of them are 107gb[/SIZE]
[SIZE=2][COLOR=#cc0000](08:42:52 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] and the other is 112 gb[/SIZE]
[COLOR=#204a87][SIZE=2](08:43:10 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok, let's be calm[/SIZE]
[COLOR=#204a87][SIZE=2](08:43:16 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]*boiling inside*[/SIZE]
[COLOR=#204a87][SIZE=2](08:43:24 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]relax.....[/SIZE]
[SIZE=2][COLOR=#cc0000](08:43:25 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] just kicked the dog[/SIZE]
[COLOR=#204a87][SIZE=2](08:43:28 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]*wants to kill*[/SIZE]
[SIZE=2][COLOR=#cc0000](08:43:31 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] the neighbor's dog[/SIZE]
[SIZE=2][COLOR=#cc0000](08:43:39 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] and by dog i mean neighbor[/SIZE]
[SIZE=2][COLOR=#cc0000](08:43:42 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :D[/SIZE]
[COLOR=#204a87][SIZE=2](08:44:05 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]wtf is your HD doing [/SIZE]
[COLOR=#204a87][SIZE=2](08:44:08 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok... let's see[/SIZE]
[SIZE=2][COLOR=#cc0000](08:44:28 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] no clue[/SIZE]
[COLOR=#204a87][SIZE=2](08:44:29 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]tell me what each drop down says exactly[/SIZE]
[COLOR=#204a87][SIZE=2](08:44:34 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]from start to finish[/SIZE]
[COLOR=#204a87][SIZE=2](08:44:40 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]from the top down[/SIZE]
[COLOR=#204a87][SIZE=2](08:44:48 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and which mount parts they are[/SIZE]
[SIZE=2][COLOR=#cc0000](08:45:06 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] well, the mount point drop downs give me the options for /, swap, home, etc.[/SIZE]
[SIZE=2][COLOR=#cc0000](08:45:23 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i wish i could send u a screen shot of this[/SIZE]
[COLOR=#204a87][SIZE=2](08:45:27 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]me too[/SIZE]
[COLOR=#204a87][SIZE=2](08:45:31 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]got a camera ?[/SIZE]
[COLOR=#204a87][SIZE=2](08:45:39 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]camera phone ?[/SIZE]
[COLOR=#204a87][SIZE=2](08:45:48 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]banana phone ?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:46:08 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] how 'bout i send it to my ubuntu thread and edit my last post?[/SIZE]
[COLOR=#204a87][SIZE=2](08:46:23 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok[/SIZE]
[COLOR=#204a87][SIZE=2](08:47:11 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]you could also, post part of this conversation, so that people can see what we've been doing[/SIZE]
[COLOR=#204a87][SIZE=2](08:47:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and get advice[/SIZE]
[COLOR=#204a87][SIZE=2](08:47:36 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]though I believe that up until this point, you've done what I did initially.[/SIZE]
[COLOR=#204a87][SIZE=2](08:47:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I don't know what is going on w/your system[/SIZE]
[COLOR=#204a87][SIZE=2](08:48:00 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and why it's seeing those things[/SIZE]


---

### Post by Sweet Spot on 2007-03-13
Continued: > [SIZE=2][COLOR=#cc0000](08:48:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] it's like a teenager:[/SIZE]
[COLOR=#204a87][SIZE=2](08:48:23 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]then you need to spank it[/SIZE]
[SIZE=2][COLOR=#cc0000](08:48:25 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i tell it to do one thing, and it does another[/SIZE]

[SIZE=2][COLOR=#cc0000](08:49:01 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i went back to the prepare partitions screen.[/SIZE]
[COLOR=#204a87][SIZE=2](08:49:01 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]..[/SIZE]
[COLOR=#204a87][SIZE=2](08:49:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]you see something amiss there ?[/SIZE]
[SIZE=2][COLOR=#cc0000](08:49:33 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] those 3 subpartitions now show up as unknown filesystems,[/SIZE]
[COLOR=#204a87][SIZE=2](08:49:42 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]wtf[/SIZE]
[SIZE=2][COLOR=#cc0000](08:49:42 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] but the sizes as i allocated them[/SIZE]
[COLOR=#204a87][SIZE=2](08:49:47 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]oh, yeah[/SIZE]
[SIZE=2][COLOR=#cc0000](08:49:49 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] wtf, indeed[/SIZE]
[COLOR=#204a87][SIZE=2](08:49:56 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]well, they are unknown, cus they're not formatted yet[/SIZE]
[SIZE=2][COLOR=#cc0000](08:50:22 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i went forward and now i have only 2 partitions of 107gb each[/SIZE]


[COLOR=#204a87][SIZE=2](09:00:41 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]hey, when you right click on one of the "unknowns" do you have any options to format or anything ?[/SIZE]
[COLOR=#204a87][SIZE=2](09:03:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]also, in the screen shot before that one, in the post above, it looks like you had it going ?[/SIZE]
[COLOR=#204a87][SIZE=2](09:03:48 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so I think that you may have forgotten a step before you skipped ahead to the mount point screen[/SIZE]
[SIZE=2][COLOR=#cc0000](09:05:21 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] sorry--had stepped away a sec[/SIZE]
[SIZE=2][COLOR=#cc0000](09:06:17 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] when i right click an unkown, it gives me the option to create a new one, delete, unmount, or deactivate[/SIZE]
[COLOR=#204a87][SIZE=2](09:07:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]hmm... unmount one of them[/SIZE]
[COLOR=#204a87][SIZE=2](09:07:23 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]out of curiosity[/SIZE]
[SIZE=2][COLOR=#cc0000](09:07:30 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] it won't let me: could notunmount[/SIZE]
[COLOR=#204a87][SIZE=2](09:07:33 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]k[/SIZE]
[COLOR=#204a87][SIZE=2](09:07:38 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]deactivate[/SIZE]
[SIZE=2][COLOR=#cc0000](09:07:41 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] no such file or directory[/SIZE]
[SIZE=2][COLOR=#cc0000](09:07:59 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] can't deactivate--invalid argument[/SIZE]
[COLOR=#204a87][SIZE=2](09:08:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]oooooo k[/SIZE]
[SIZE=2][COLOR=#cc0000](09:08:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] delete and start again?[/SIZE]
[COLOR=#204a87][SIZE=2](09:08:18 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]lemmie think[/SIZE]
[SIZE=2][COLOR=#cc0000](09:08:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Jebus![/SIZE]
[COLOR=#204a87][SIZE=2](09:08:32 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]there's something else we're missing ere[/SIZE]

[SIZE=2][COLOR=#cc0000]([/COLOR][/SIZE]
[SIZE=2][COLOR=#cc0000](09:10:46 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] HEY!!![/SIZE]
[SIZE=2][COLOR=#af7f00]([/COLOR][/SIZE]
[COLOR=#204a87][SIZE=2](09:11:49 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]wha ?[/SIZE]

[SIZE=2][COLOR=#cc0000](09:12:24 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i clicked forward again and the mount point screen lets me select mount points in drop down menus and select the partition in the drop down next to it....[/SIZE]

[COLOR=#204a87][SIZE=2](09:12:41 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Yeah, I know...that's what you are supposed to do[/SIZE]
[SIZE=2][COLOR=#cc0000](09:12:43 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] gotta be a client issue[/SIZE]
[COLOR=#204a87][SIZE=2](09:12:50 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]you didn't have that option before ?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:12:51 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] well, **** me runnin'![/SIZE]
[SIZE=2][COLOR=#cc0000](09:13:04 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] lemme try to tell it to do what i thought i was....[/SIZE]
[SIZE=2][COLOR=#cc0000](09:13:07 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :D[/SIZE]
[COLOR=#204a87][SIZE=2](09:13:08 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Id rather you be at least sitting to be honest, [/SIZE]
[SIZE=2][COLOR=#cc0000](09:13:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] Jebus....[/SIZE]
[COLOR=#204a87][SIZE=2](09:13:37 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]does this mean that we're making some freeking headway ?[/SIZE]
[COLOR=#204a87][SIZE=2](09:13:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I'll be filled with glee if you say yes[/SIZE]
[COLOR=#204a87][SIZE=2](09:14:03 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]furthermore, I'll be filled with pee, if you say no[/SIZE]
[SIZE=2][COLOR=#cc0000](09:15:00 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i think so...screen shot?[/SIZE]
[COLOR=#204a87][SIZE=2](09:15:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]por favor[/SIZE]
[SIZE=2][COLOR=#cc0000](09:15:48 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] trying--i'll just bump....[/SIZE]
[COLOR=#204a87][SIZE=2](09:15:58 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]nah, just edit it[/SIZE]
[SIZE=2][COLOR=#cc0000](09:16:03 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] k[/SIZE]
[COLOR=#204a87][SIZE=2](09:16:05 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]like a GOOD forum member ![/SIZE]

[SIZE=2][COLOR=#cc0000](09:18:29 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] heh--i dinna realize i could just manage the attachments[/SIZE]
[SIZE=2][COLOR=#cc0000](09:19:06 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] HUZZAH![/SIZE]
[SIZE=2][COLOR=#cc0000](09:19:32 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] is daddy good ta go?  do i check reformat?[/SIZE]
[COLOR=#204a87][SIZE=2](09:19:46 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]Oh... I think I get it now[/SIZE]
[COLOR=#204a87][SIZE=2](09:20:10 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]there's two 107 gb things because one is the extension of the primary, I THINK[/SIZE]
[COLOR=#204a87][SIZE=2](09:20:14 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]or some **** like that[/SIZE]
[COLOR=#204a87][SIZE=2](09:20:40 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]make sure to click the reformat boxes on the right of them ![/SIZE]
[COLOR=#204a87][SIZE=2](09:21:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]wait...[/SIZE]
[COLOR=#204a87][SIZE=2](09:22:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]the 107 gb's...isn't that the windows partition ?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:22:12 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] only my root, swap, and home ones, right?  the 107gbs are my windows....[/SIZE]
[SIZE=2][COLOR=#cc0000](09:22:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] yes..why are there 2?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:22:49 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] one is SATA 2 and the other is SATA 1...?[/SIZE]
[COLOR=#204a87][SIZE=2](09:22:52 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]because it sees them. but don't worry, as long as you only check the boxes which need formatting, it doesn't matter[/SIZE]
[SIZE=2][COLOR=#cc0000](09:23:15 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] sooo...[/SIZE]
[SIZE=2][COLOR=#cc0000](09:23:20 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] ...shall i....?[/SIZE]
[COLOR=#204a87][SIZE=2](09:23:26 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so, check the last 3[/SIZE]
[COLOR=#204a87][SIZE=2](09:23:40 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]the 12, 2 and 125[/SIZE]
[SIZE=2][COLOR=#cc0000](09:23:47 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] yup...otherwise i'll bugger xp--again![/SIZE]
[SIZE=2][COLOR=#cc0000](09:23:52 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] so forward?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:00 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i'm scared, dougie![/SIZE]
[COLOR=#204a87][SIZE=2](09:24:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]i I ....I  IIIII I think so ![/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:09 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :-S[/SIZE]
[COLOR=#204a87][SIZE=2](09:24:09 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]me tooooooo[/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:18 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] **** it...all of it...[/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:27 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] FORWARD HOOOOOOOOO!!!!!!!![/SIZE]
[COLOR=#204a87][SIZE=2](09:24:31 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]#-o[/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:40 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] stand back![/SIZE]
[COLOR=#204a87][SIZE=2](09:24:40 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]8-X[/SIZE]
[SIZE=2][COLOR=#cc0000](09:24:49 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i dunno how big this thing gets!!!![/SIZE]
[SIZE=2][COLOR=#cc0000](09:25:00 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] "install"??????[/SIZE]
[SIZE=2][COLOR=#cc0000](09:25:02 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] :D[/SIZE]
[COLOR=#204a87][SIZE=2](09:25:04 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]<:-P[/SIZE]
[SIZE=2][COLOR=#cc0000](09:25:10 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] lemme think...[/SIZE]
[COLOR=#204a87][SIZE=2](09:25:19 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5];))[/SIZE]
[SIZE=2][COLOR=#cc0000](09:25:20 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] HELLZORS YESZORS!!!!![/SIZE]
[SIZE=2][COLOR=#cc0000](09:25:43 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] ...installing...[/SIZE]
[COLOR=#204a87][SIZE=2](09:25:48 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]come on BABY ![/SIZE]
[COLOR=#204a87][SIZE=2](09:25:57 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]L33t[/SIZE]
[SIZE=2][COLOR=#cc0000](09:26:21 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] 10%[/SIZE]
[COLOR=#204a87][SIZE=2](09:26:34 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]did you go through this before ?[/SIZE]
[COLOR=#204a87][SIZE=2](09:26:40 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yeah, you did I believe[/SIZE]
[COLOR=#204a87][SIZE=2](09:27:08 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]****, I'm hungry[/SIZE]
[SIZE=2][COLOR=#cc0000](09:30:56 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] yes, but i dinna change any drop down screen in the mount point...i just hit forward....[/SIZE]
[SIZE=2][COLOR=#cc0000](09:31:05 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] have you had supper?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:31:14 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] 93%!!!![/SIZE]
[COLOR=#204a87][SIZE=2](09:31:34 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]not really. had some cheese and crackers. and a BIT of pasta when i got home at 5[/SIZE]
[COLOR=#204a87][SIZE=2](09:31:44 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]yay ! I think this is going to work ![/SIZE]
[COLOR=#204a87][SIZE=2](09:31:55 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I think this is SO going to work ![/SIZE]
[SIZE=2][COLOR=#cc0000](09:32:00 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] install complete.[/SIZE]
[COLOR=#204a87][SIZE=2](09:32:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]F'n A ![/SIZE]
[COLOR=#204a87][SIZE=2](09:32:12 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok....[/SIZE]
[COLOR=#204a87][SIZE=2](09:32:15 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]what's next[/SIZE]
[SIZE=2][COLOR=#cc0000](09:32:26 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] On restart, should i not get something that lets me choose the OS?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:32:37 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] or do i hafta go into a boot menu?[/SIZE]
[COLOR=#204a87][SIZE=2](09:32:44 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]are you being prompted to do anything now ?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:32:53 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] a choice:[/SIZE]
[COLOR=#204a87][SIZE=2](09:32:59 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]do tell[/SIZE]
[SIZE=2][COLOR=#cc0000](09:33:10 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] either: continue using live cd, or; restart now[/SIZE]
[COLOR=#204a87][SIZE=2](09:33:15 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]restart[/SIZE]
[SIZE=2][COLOR=#cc0000](09:33:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] restart now!!!![/SIZE]
[COLOR=#204a87][SIZE=2](09:33:24 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]I think it will eject the cd[/SIZE]
[COLOR=#204a87][SIZE=2](09:33:28 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]so watch for that[/SIZE]
[SIZE=2][COLOR=#cc0000](09:33:34 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] k--we shall soon see[/SIZE]
[COLOR=#204a87][SIZE=2](09:33:38 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]and yes, you should get the grub boot menu[/SIZE]
[COLOR=#204a87][SIZE=2](09:33:43 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]watch for that too[/SIZE]
[SIZE=2][COLOR=#cc0000](09:33:57 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] that's right...it prompts me to do that, then press enter.[/SIZE]
[COLOR=#204a87][SIZE=2](09:34:14 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]both the grub menu as well as the log on screen can be altered/modded significantly[/SIZE]
[SIZE=2][COLOR=#cc0000](09:34:19 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] disc our[/SIZE]
[SIZE=2][COLOR=#cc0000](09:34:25 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] waiting[/SIZE]
[SIZE=2][COLOR=#cc0000](09:35:08 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] ****[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:09 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]for the record, all of the script stuff you'll see as it loads each time, is the same crap that goes on in the background of Windows too. Most people leave their Linux boxes on, so the load time doesn't bother them[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:15 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]what ?[/SIZE]
[SIZE=2][COLOR=#cc0000](09:35:25 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] wondows booted up[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:27 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]please don't tell me it's boo[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:29 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]****[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:37 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]you told me[/SIZE]
[COLOR=#204a87][SIZE=2](09:35:44 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]ok....[/SIZE]
[COLOR=#204a87][SIZE=2](09:36:07 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]hard boot[/SIZE]
[COLOR=#204a87][SIZE=2](09:36:09 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]again[/SIZE]
[SIZE=2][COLOR=#cc0000](09:36:16 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] i dinna see grub during the black start up screens[/SIZE]
[SIZE=2][COLOR=#cc0000](09:36:30 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] hard boot=power button?[/SIZE]
[COLOR=#204a87][SIZE=2](09:36:35 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]sec[/SIZE]
[COLOR=#204a87][SIZE=2](09:36:37 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=5]lemmie think

[SIZE=3]Where to go from here ?[/SIZE]
[/SIZE]

---

### Post by BigBabyDaddy1968 on 2007-03-13
And please pardon my French in that conversation... :D  A bit frustrated with myself.

OK, I went back in and have gotten back to the mount point screen.  I also used the commands suggested above and this time when I checked for GRUB, I got this:

---

### Post by Sweet Spot on 2007-03-13
Also: > [SIZE=3] [/SIZE][SIZE=5]something tells me that what you said about your HD ghost backing your stuff up...may be screwing something[/SIZE]
[COLOR=#204a87][SIZE=2](10:08:27 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] [/SIZE][SIZE=5]technically, there should not be TWO mount points for Win[/SIZE]
[SIZE=2][COLOR=#cc0000](10:08:31 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] That is what i suspect, but how to get rid of it.[/SIZE]
[COLOR=#204a87][SIZE=2](10:08:45 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] [/SIZE][SIZE=5]ok, try going into your set up screen again F12[/SIZE]
[COLOR=#204a87][SIZE=2](10:09:03 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] [/SIZE][SIZE=5]look at any possible options pertaining to that particular feature. [/SIZE]
[COLOR=#204a87][SIZE=2](10:09:10 PM) [/SIZE]**[SIZE=3]DRB:[/SIZE]**[/COLOR][SIZE=3] [/SIZE][SIZE=5]if you can shut if off, please do so[/SIZE]
[SIZE=2][COLOR=#cc0000](10:09:11 PM) [/COLOR][/SIZE][COLOR=#cc0000]**[SIZE=3]bigbabydaddy1968:[/SIZE]**[/COLOR][SIZE=3] it is a "data safe" hd...not sure what it means beyond it is supposed to act as a backup in case of a crash....[/SIZE]

---

### Post by Sweet Spot on 2007-03-13
For the record, my Gparted screen shot, and where I've been guiding him from;

---

### Post by BigBabyDaddy1968 on 2007-03-13
The latest: the 107gb partition is what I created for windows, the rest is self explanatory for anyone...but me, it seems....  I have no idea why it chose to number the others as partitions 7, 5, and 6.

---

### Post by BigBabyDaddy1968 on 2007-03-13
OK, problem seems solved.  My HD has a sort of "ghost" backup for the hd which shows up as the same size and device id.  When I disabled SATA1 and rebooted, I got the choice to go to UBUNTU or windows....  It seems that was the problem all along.

**NEW PROBLEM:** no browser connection.  Do I need to install drivers for my ethernet card?  Am I missing something obvious?

---

### Post by Sweet Spot on 2007-03-14
oops, wrong reply

---

### Post by BigBabyDaddy1968 on 2007-03-14
Hardware screenshot....

---

