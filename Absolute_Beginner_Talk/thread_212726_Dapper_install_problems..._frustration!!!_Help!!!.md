---
title: "Dapper install problems... frustration!!! Help!!!"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-07-10
Hey everyone,

I played around with Dapper at home, seems to work perfectly well. I ordered the cds from shipit and I decided to install it on my computer at work. Works well from CD though a bit slow because I have slightly less than 256 MB ram.

I have two HDs, one 40GB and one 80GB. The 40GB has three partitions, C, D and E on windows and the 80 GB has two 40GB partitions, F and G on windows. G is empty and free at the moment.

I backed up the data on F so my 80GB disk is backed up.

Then I put in the CD and double-clicked the install icon on the desktop and went through steps 1-4 no problem.

Then the partitioning part came up. It showed me both HDs, 40GB as hdc and 80GB as hda.

So I chose hda. It then gave me the graphical %ge chooser thing, but even if I slide it all the way to 100% it gives me only 40GB. So for one thing, I'm not sure if it's choosing F or G. it says ext1 partition#5 and shows me the partition as hd5. 

Anyways, I've backed up my data and have nothing to lose even if it's F that it's choosing so I go ahead and click next and the computer hangs. I read that it might hang for a while so I went out, grabbed some coffee and came back a while later but the computer's still stuck... no response from mouse or keyboard at all.

This is about the 3rd or 4th time I tried this today. ](*,) I also tried manuwally partitioning after which I'm presented with a black area in my window and the system hangs again.

Any suggestions?[-o< 

Is there any way I can do this from a text-based console instead of the graphical one?

Thanks in advance. You guys are great.

Cheers,
David

---

### Post by lordlollo on 2006-07-10
> **dckirba said:**
> Is there any way I can do this from a text-based console instead of the graphical one?

Of course, but I think you'll need the alternate install cd... And this could be a problem, if you plan to rely only on the ship_it delivery service...

---

### Post by dckirba on 2006-07-10
Ouch! that's not good. Internet is too slow to download huge files and I really have to rely on the Shipit CDs...

---

### Post by molly_001 on 2006-07-10
In my experience, if you are using the LiveCD (Desktop 386) and it only lets you select the 100% slider option, then the LiveCD installer is going to give you further grief from that point forward.  Abort.

You are much better off to use the alternate install CD as mentioned above by lordlollo.  You'll receive many more options and functionality to create just the layout of partitions you desire according to taste.
In such a case, you wouldn't want to make a move without consulting Herman's defacto universal guide to dual boot NTFS + Ubuntu, found here: [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Also in my experience ... you are perfectly set up to run Ubuntu and Windows on your 80GB as primary drive, allowing the 40GB to sit on the sidelines without an OS, always at the ready to be the go-to drive for backups.  This is what I do on my machines, and I absolutely love it, one click and I get to back up my data from both my 80GB/hda0/NTFS/primary and 80GB/hda1/Ubuntu/primary.   (I used 80GB and hda0/hda1 merely in an illustrative manner in the previous comment, to match your hardware.)

---

### Post by dckirba on 2006-07-10
Hi Molly,

Well, it does give me more options than 100%. I'm just a bit confused because when I initially choose which Hd to install on I'm choosing my 80GB hd with two 40GB partitions. I want to install on the second partition, but I don't know which partition I'm choosing from then on as there's no way to know. It does however let me move the slider down and up. 100% gives me around 40Gig. 

Is installing from the live CD usually problematic or is it just that I have low memory (256) on this system?

cheers,
David

---

### Post by molly_001 on 2006-07-10
With your most recent post, I can better understand the situation you are looking at there.  It's ironic (and inconvenient) that everything appears as 40GB based on your partitions.  (Just a note: I've had this problem before, so now on any machine, no matter what OS, I always make my partitions of different sizes, say 45 and 35.  Lesson learned for me!)

So here is the answer to your question: The LiveCD installer will not install onto (overwrite) your existing NTFS partition wherein a NTFS boot exists on that partition.  It needs to keep that partition so that it will be able to refer the MBR on the hard disk to it, thus giving you that dual boot option.  So even though you can't tell at the moment (due to equivalent 40/40 split) you can proceed knowing that it will install onto 'that other' non-XP install partition.

Of course, before doing anything at all, you want to have a 100% backup of all your data from your Windows XP partition.  You can always reinstall programs and reinstall XP in case disaster strikes.  But you want a 100% backup of your data accomplished first.

---

### Post by lordlollo on 2006-07-10
> **molly_001 said:**
> But you want a 100% backup of your data accomplished first.
Yes, imo this is the crowning suggestion :KS

---

### Post by dckirba on 2006-07-10
> **molly_001 said:**
> The LiveCD installer will not install onto (overwrite) your existing NTFS partition wherein a NTFS boot exists on that partition.  It needs to keep that partition so that it will be able to refer the MBR on the hard disk to it, thus giving you that dual boot option.  

Hi Molly,

On this system, windows is installed on another HD (40 GB capacity in total with 3 partitions, 10Gb, 10GB and 20GB)

I'm trying to install on another HD (80GB with two 40GB partitions). One partition I use for some documents and the other is free.

My question is, does this mean that Ubuntu will install only on the same HD as windows or will it work on the other one?

My main problem at the moment is that it gets stuck halfway through the installation process. I checked the psychocats website and it says min. requirements to install from the Desktop is 196MB Ram and I have around 230MB. 

More suggestions very welcome,

Thankyou so much for your time and patience, I am very new to this,

Cheers,
David K

---

### Post by smile-its-smiley on 2006-07-10
i had very similar problems it installed fine on my desktop and got stuck on my laptop at abou 40% i found it was my cd was faulty so i just burnt a new one and it worked do you know any one with broadband they might let you to download it

---

### Post by dckirba on 2006-07-10
Hey smile,

I do have another copy of the cd left over from what Shipit sent me. I did however check the cd before I started the install and everything was fine. I am trying to download the alternate version... looks like it'll take 5-10 days if I'm downloading during office hours :) No broadband here! C'est la vie :)

I am going to try installing again and see what happens this time.

Cheers,
David K

---

### Post by molly_001 on 2006-07-10
You really should just use the LiveCD of Gparted, the LiveCD of GAG Boot Manager, and the Alternate install CD for Ubuntu.

I feel for ya' being without decent internet access.  I've traveled most of the Middle East and have often times run into that frustration.

If you go to my site, we can arrange to have all three mailed to you in Addis Ababa.  You'll need to reflect whether you are willing to Paypal the shipping amount -- in advance, of course, but it would be for mailing costs (per whatever method you wish them to be mailed to you.)

Also, if you have a DVD-ROM, then I have all three of those DVDs already burned and sitting here on my desk, which means I could mail them tomorrow.

---

### Post by dckirba on 2006-07-11
Hey Molly!

Thankyou, that is really nice of you. Unfortunately, I don't have Paypal and won't be able to pay you for the postage. However, it's mainly the computer at work that's giving me the headache and I have started downlaoding the alternate CD. I hope the download manager gets it down in one piece :) Got to 5% so far! But it'll get here eventually and then I'll give it a go. My computer at home has 512 MB Ram and handles the live cd well so I'm hoping it'll install fine on that when I get another HD for it, which should be in a few weeks when i get my salary :) 

Once again, thankyou so much for your help and your offer. Much appreciated!

Have a good one,
Cheers,
david K

---

