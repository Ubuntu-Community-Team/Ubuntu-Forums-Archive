---
title: "Make Music CD - I am lost [Resolved]"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-05-30
I'm lost. I'd like to burn a music CD from a collection of MP3 files. I've found no info on the Serpentine site. I've read here that I should first make a playlist with Rhythmbox? I've looked at the Rhythmbox Help, but no instructions on how to make a playlist.

I don't understand any of what's been said about this topic. The learning curve remains steep  :-)

How do I burn a CD from a collection of MP3 files. I don't want to simply write the files on a disk, I want to make a CD that plays from start to finish - in a common CD player. I tried adding some of the MP3 files to Serpentine, but it gives messages I don't understand about them being the wrong file type.

Can you offer some simple instructions? Thanks much.

---

### Post by RichPicker on 2007-05-31
Bump

---

### Post by jfinkels on 2007-05-31
> **RichPicker said:**
> I'm lost. I'd like to burn a music CD from a collection of MP3 files. I've found no info on the Serpentine site. I've read here that I should first make a playlist with Rhythmbox? I've looked at the Rhythmbox Help, but no instructions on how to make a playlist.

I don't understand any of what's been said about this topic. The learning curve remains steep  :-)

How do I burn a CD from a collection of MP3 files. I don't want to simply write the files on a disk, I want to make a CD that plays from start to finish - in a common CD player. I tried adding some of the MP3 files to Serpentine, but it gives messages I don't understand about them being the wrong file type.

Can you offer some simple instructions? Thanks much.

Are you able to play mp3 files? You may need to install the appropriate codecs! See here for some info on that; this might be the reason you're getting an error message.

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

> **RichPicker said:**
> Bump

Don't bump posts that are only an hour old! Give us some time here! :D

---

### Post by RichPicker on 2007-05-31
Yes I can play MP3 files.

The error message serpentine gives is this:

You can only use growisofs on a data or graft list track

????
.

---

### Post by jfinkels on 2007-05-31
> **RichPicker said:**
> Yes I can play MP3 files.

The error message serpentine gives is this:

You can only use growisofs on a data or graft list track

????
.

What kind of drive do you have (CD-RW? DVD-RW?) and what kind of media are you trying to burn to (CD-R? CD-RW? DVD-R?)?

---

### Post by RichPicker on 2007-05-31
DVD=RW drive
Trying to burn a CD-R

I can burn a CD with the collected MP3 files, but not a "CD' that plays on a CD player with Serpentine. I can only make a CD with a collection of data files.

---

### Post by RichPicker on 2007-05-31
I add music (MP3) files to Serpentine, click Make CD, and the error message appears

---

### Post by irish_flu on 2007-05-31
Hmmm, there must be something afoot; I just drag my tracks into Serpentine, then burn the CD.

It might not hurt to reinstall Serpentine in Synaptic; maybe there's something missing that it needs (that's just a guess)?

---

### Post by RichPicker on 2007-05-31
I reinstalled it, but no go. I get this error message:

Writing to Disk Failed
Can only use growisofs on a single track

????   What the heck are growisofs anyway?

---

### Post by mozetti on 2007-05-31
growisofs - [http://www.linuxcommand.org/man_pages/growisofs1.html](http://www.linuxcommand.org/man_pages/growisofs1.html)
I didn't read it, but found it on Google.

I use gnomebaker for making CDs, that's my suggestion.

---

### Post by RichPicker on 2007-05-31
Gnomebaker ALMOST wrote the CD. It got to the end, and then failed. Oh well... Another wasted disk. I really do appreciate your help, but you know what? Ubuntu is ****. It's the most problematic, troublesome OS I have ever used. Open source definitely has advantages over licenses microsoft. But at least microsoft WORKS. 

Ubuntu, you must hammer and tweak and modify and work and work and work. It really is a nuisance piece of ****., I don't care if I'm scolded. What I'm saying it the truth.

---

### Post by mozetti on 2007-05-31
[http://ubuntuforums.org/showthread.php?t=459797](http://ubuntuforums.org/showthread.php?t=459797)

---

### Post by orange2k on 2007-05-31
Try K3B...works very nice here :D

---

### Post by tact on 2007-05-31
the file format of MP3 and raw audio tracks on an audio CD are very different.

you need to use "ripping" software to convert audio CD tracks to MP3 format.

to convert back the other way from MP3 to audio CD track file format  - guess what... u need a converter too. 

If you just open an "audio cd" project and drop a load of MP3 files there...  (in gnomebaker and the inbuild CD/DVD burning facility in nautilus(?)) - guess what...  there is no conversion I can see.  So you end up with a CD of separate MP3 files.  Same as if you created a "data cd" and burned all MP3 files.

My car CD player can play a "data" cd full of MP3 files and I love it.  One CD 280 songs.  I carry 3 CDs on long trips.  Instead of 60 normal Audio CDs

I would suggest that instead of burning off ubuntu because soem CD burning applications do NOT perform magical unrequested file format transforms for you...  you look at what may be the real problem....  

i.e... find a tool to convert MP3 to normal audio track file format...    (like you had to find a tool to rip the audio CD to MP3 in the first place)

then burn your CD tossing the audio tracks as opposed to MP3 files.

(guess what - the process would be the same in WinXP..  I do not think that media player or even Nero will on the fly convert your MP3s to audio tracks either!)

SOrry I cannot help you find the needed tool.  I have never had a need to "unrip" (?) MP3's back to audio tracks.

---

### Post by carloslosgrande on 2007-05-31
There are quite a few cd/dvd writers available. I've used Gnomebaker and its really good, so is K3b which I use now because it does some extra things I need. Its also really simple, like me.
I've no idea what a 'growisofs' is.

---

### Post by tact on 2007-05-31
perhaps there are no tools to convert mp3 or other formats back to .CDA (audio tracks).

doing what you should have done I googled and found too much information to dig deeply.

try reading this page for information.  notice there are many tools to convert .CDA to other formats but I didnt see any going back the other way.

let me know if you can do what you say you so much want to do in windows....
(ie convert MP3's back to normal audio cd format (.CDA) and burn to a CD that will then play back fine in a normal audio music cd player.)

---

### Post by RichPicker on 2007-05-31
GnomeBaker:

First it converts the MP3 files to CD Audio files.
Then it Prepares to Burn Disk
Then it writes tracks 1, 2, . . .  etc.
Then when the percentage-complete counter reaches approx. 89%,  it Fails.

Here is the error message:  (Is it a problem with the size of the buffer????)

Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Starting new track at sector: 206528
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 06 2D 35 00 00 0D 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 63 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x63 Qual 0x00 (end of user area encountered on this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 30576
cmd finished after 0.000s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

WARNING: padding up to secsize.
write track data: error after 466309872 bytes
Writing  time:  211.335s
Average write speed   3.3x.
Min drive buffer fill was 70%
Fixating...
Fixating time:   28.790s

---

### Post by RichPicker on 2007-05-31
I've tried Serpentine and GnomeBaker. Serpentine fails also, but with a different error message.

I've written tons of data to CDs with this system, and copied several DVD movies. But it won't do the things necessary to burn a music CD. 

I'll ask launchpad.

---

### Post by RudolfMDLT on 2007-05-31
Lets just try a completely different suite - The reason I want you to try K3B is that it's a very cool new version that came out with Ubuntu 7.04. The errors are clear and it'll give detailed info on what burner you are using.

---

### Post by Hobo Joe on 2007-05-31
```

sudo aptitude install gnomebaker
gnomebaker

```

Then click audio CD. Tada! It works!

---

### Post by RudolfMDLT on 2007-05-31
Asui has moved my post here,

so how about it? I've just installed GnomeBaker and I'm currently burning an Audio disc - will post the outcome. Now please install K3B, it has much better info for Hardware and errors!

---

### Post by aysiu on 2007-05-31
I Googled your error message (*wodim: A write error occured*) and found [this fix](http://ubuntuforums.org/showthread.php?p=2746112#post2746112). Hope that helps.

---

### Post by RudolfMDLT on 2007-05-31
Aysdiu seems to have found something - give it a try man.

---

### Post by fjf on 2007-05-31
Well, if you did that with windoze, there is also nerolinux....The windoze version does this job of converting mp3 to CDs very well...

---

### Post by jonward0690 on 2007-05-31
I had all kinds of problems using serpintine i use eather gnome baker or brasero to burn cds.

---

### Post by RichPicker on 2007-05-31
Thanks, folks. I'll load the updates the next time I'm on a high-speed connection. It would take a day to do it with this slow modem.

I turned the Update Notifier off. In March, I had everything running in Edgy (I run Feisty now, though my [profile doesn' say it), and an update was released that killed my ability to use the microphone and killed google earth. Seems that updates are distributed without first checking to see who it will effect.

I'll take a chance and load the updates. Then see if the CD burner works, Then post here again.

Does this ever stop? Do you EVER get the machine set up with Ubuntu, and then just use it without these constant struggles? I hope to use the web camera some day, but fear that will be an even larger headache getting it to work.

Thanks again for you help. You certainly have better luck finding things with google than I do. Oh well Thank you much. Multumesc fuarte mult.

Peace,
R-

---

### Post by jfinkels on 2007-05-31
> **RichPicker said:**
> Thanks, folks. I'll load the updates the next time I'm on a high-speed connection. It would take a day to do it with this slow modem.

I turned the Update Notifier off. In March, I had everything running in Edgy (I run Feisty now, though my [profile doesn' say it), and an update was released that killed my ability to use the microphone and killed google earth. Seems that updates are distributed without first checking to see who it will effect.

I'll take a chance and load the updates. Then see if the CD burner works, Then post here again.

Does this ever stop? Do you EVER get the machine set up with Ubuntu, and then just use it without these constant struggles? I hope to use the web camera some day, but fear that will be an even larger headache getting it to work.

Thanks again for you help. You certainly have better luck finding things with google than I do. Oh well Thank you much. Multumesc fuarte mult.

Peace,
R-

Developers (and testers, who are in fact all of us!) do their best to make sure their products are stable and effective. Many of the problems you will find people have are hardware problems. An unlucky combination of hardware may cause an unpleasant experience (as in your case), but many, many people have had quite an easy setup and usage experience! Remember, Ubuntu is (as all software is, really) a work in progress! You can help by filing bug reports where appropriate and encouraging hardware manufacturers to distribute open source Linux drivers with their devices.

As for your current problem, aysiu seems to have found an appropriate solution. Let us know if you need help installing the 2.6.20-16 kernel!

---

### Post by RichPicker on 2007-05-31
Well, thank you. I don't know if I need help installing the new kernel. I assumed it's in the Updates. No? I checked Update Manger, and it said it would take more than one day to install them Should I pick only the new kernel? Is it obvious? I will google and see if I can find instructions on installing the new kernel. Thank you.

---

### Post by jfinkels on 2007-05-31
> **RichPicker said:**
> Well, thank you. I don't know if I need help installing the new kernel. I assumed it's in the Updates. No? I checked Update Manger, and it said it would take more than one day to install them Should I pick only the new kernel? Is it obvious? I will google and see if I can find instructions on installing the new kernel. Thank you.

Just do ```
sudo aptitude update && sudo aptitude upgrade
```

It may take a long time if you're on a modem!

If it gives you some goofy message about "holding back" packages, let us know.

---

### Post by RichPicker on 2007-05-31
Look at this  [http://ubuntuforums.org/showthread.php?t=457328](http://ubuntuforums.org/showthread.php?t=457328)    it seems that new problems happen with this new kernel. Will that happen with this machine. Sheesh. Does this struggle ever end? The solution is offered, and along with it comes more problems.

Please help. This is a mess.

---

### Post by pappapump on 2007-05-31
I think your'e missing the obvious here.
Your problem seems to be in finalizing the disc OR finishing your lead out and final write.
A lot of times this is caused by a writer that rarely uses the full length of the guide pin which the laser head travels on.
When that happens, dust settles into the lubricant coating the spindle/pin.
In generic writers and sony writers this happens a lot.
One way to test that is to make a minimal CD with about half as many MP3 files as you would normally convert.
Try to write, then if the write is successful you know that the CDRW is at fault.
The cost of this method is a single CD and a rather speedy write.

---

### Post by RichPicker on 2007-05-31
Wow,. That's an incredible suggestion. I will try it now.

---

### Post by tomdkat on 2007-05-31
> **pappapump said:**
> I think your'e missing the obvious here.
Your problem seems to be in finalizing the disc OR finishing your lead out and final write.
A lot of times this is caused by a writer that rarely uses the full length of the guide pin which the laser head travels on.
When that happens, dust settles into the lubricant coating the spindle/pin.
In generic writers and sony writers this happens a lot.
One way to test that is to make a minimal CD with about half as many MP3 files as you would normally convert.
Try to write, then if the write is successful you know that the CDRW is at fault.
The cost of this method is a single CD and a rather speedy write.Would slowing down the burn speed help?  RichPicker,  I run Ubuntu 7.04 (64-bit) and haven't had any of the problems others have had with the latest kernel (or other) update(s).  I second pappapump's suggestion and also suggest slowing down the burn speed to see if that makes any difference.   I HAVE burned audio CDs from MP3 files on my internal DVD +/- RW burner onto CD-R media so it is possible.   We just need to see what's up with your particular burner and the software being used to burn the audio.

You posted earlier that you are using a DVD burner for this but you didn't post a make/model.  Can you post the make/model of your Dell?  That way, people can get an idea of the base system config and have an idea of the hardware environment you're running on.  

Good luck!

Peace...

---

### Post by pappapump on 2007-05-31
For petes sake i hope he don't have a gigabyte or a newer lite-on.
Those are buggy even in Winders, so I stopped selling em.

---

### Post by RichPicker on 2007-05-31
Gnomebaker said it worte the CD successfully. But two CD players say "No Disk". and when I put the CD back into the computer, it tells me Cannot Mount Volume.

It didn't work. Gnomrbaker said it wrote it, but it didn't.

---

### Post by RichPicker on 2007-05-31
It's the regular Sony DVD RW they put in Dell laptops.

---

### Post by RichPicker on 2007-05-31
It's a Dell Inspiron 1300. I have copied music CDs with it, copied movies with it, and wrote data on disks with it. For whatever reason, it will not burn a music CD. I will install K3B. Gnomebaker first converts the files, then writes them. It looks to be going okay for a while. Then dies. How can it copy music and movie CDs and wrtie data, but NOT write a music CD? It must be the software - or a software incompatibility.

---

### Post by RichPicker on 2007-05-31
OOps. I forgot - it's burning at 4X.

---

### Post by jfinkels on 2007-05-31
> **RichPicker said:**
> Look at this  [http://ubuntuforums.org/showthread.php?t=457328](http://ubuntuforums.org/showthread.php?t=457328)    it seems that new problems happen with this new kernel. Will that happen with this machine. Sheesh. Does this struggle ever end? The solution is offered, and along with it comes more problems.

Please help. This is a mess.

No, this should not be a problem. Issues like this are outlying cases; you won't notice all the successful cases because none of those will come to the forums looking for help :D In any case, there's no choice but to give it a try! We can fix any other problems that arise later. As the thread that aysiu posted suggests, upgrading the kernel may give you a fix.

---

### Post by pappapump on 2007-05-31
And theres your problem.
Sony=Useless.
It's a big point of debate but I have proven my point time and again.
Sony devices of various types are designed to last just so long then die.
Even if I'm wrong on THAT point, they're just plain useless at making anything with a motor.
Sure, you may be one of the lucky few who got one of the no limit chip models but inevitably the chipset on a load of sony drives fails.
I have experienced this problem also with their Televisions and have had to buy after market chips on Tv Sets older than 5 years to get them running again.
After extreme diagnoses on all components with a full pass rate I finally had to diagnose the onboard bios chip, and guess what?
It was empty except for some basic eprom code.
New Chip and violla! The humongous 3x inch beast was alive and well.
My opinion will always be, sony sux no matter what they make.
Some may disagree but anyway...................
Get a generic DVD-RW at Walmart, target or wherever and watch your CD/DVD writing become a joy again.
I use an external CD/DVD cable and power supply which i purchased dirt cheap from surplus something or another to test all of my IDE based components before install.
Worx purrrrfectly with any linux distro.

---

### Post by RichPicker on 2007-05-31
I'll load the new kernel, then post again. Thanks.

---

### Post by pappapump on 2007-05-31
> **RichPicker said:**
> It's a Dell Inspiron 1300. I have copied music CDs with it, copied movies with it, and wrote data on disks with it. For whatever reason, it will not burn a music CD. I will install K3B. Gnomebaker first converts the files, then writes them. It looks to be going okay for a while. Then dies. How can it copy music and movie CDs and wrtie data, but NOT write a music CD? It must be the software - or a software incompatibility.

Rich, that CD/DVD you have will just about always be able to be read from but the writing will continue to degrade.
Don't believe me?
Try testing it with Drive-speed in nero with your windows os using a completely full CD.
Now if youre short on cash and want to continue trying new things you can either look for a CD bios update at Sony or download one of their diagnoses apps.

---

### Post by jfinkels on 2007-05-31
> **pappapump said:**
> Rich, that CD/DVD you have will just about always be able to be read from but the writing will continue to degrade.
Don't believe me?
Try testing it with Drive-speed in nero with your windows os using a completely full CD.
Now if youre short on cash and want to continue trying new things you can either look for a CD bios update at Sony or download one of their diagnoses apps.

Ok ok, we get it :P let him update the kernel first....(should do that anyway), then we can make him spend money :D

---

### Post by carloslosgrande on 2007-05-31
I've got K3b and Amarok which both work well for me. When in amarok I select burn cd I get the options shown in the attachment.
Isn't this want you want?

---

### Post by RichPicker on 2007-05-31
I'll have to update the kernel tomorrow from the library, or wait until Saturday when they install DSL here This modem is too slow, and it drops off too frequently. I'll post again tomorrow or Saturday after I install the updates. Your time is valuable. Thank you very much for your help.

Good night,
R-

---

### Post by jcconnor on 2007-05-31
One of the things that I have had to do is use CD-R discs (I have less luck with CD+R discs) and turn down the speed to 4X burn rate using Serpentine's settings - Edit / Preferences / Writing Speed.  If I try a higher burn speed I get a similar (though not the same) error message.

---

### Post by tomdkat on 2007-06-01
> **jcconnor said:**
> One of the things that I have had to do is use CD-R discs (I have less luck with CD+R discs) and turn down the speed to 4X burn rate using Serpentine's settings - Edit / Preferences / Writing Speed.  If I try a higher burn speed I get a similar (though not the same) error message.
He's already burning at 4x speed and in the error message he posted, a burn speed of 3.3x was reported.

Maybe cranking the speed down to 2x or 1x might help.  I dunno...

Peace...

---

### Post by RichPicker on 2007-06-02
That did it. Updating the kernel fixed it. Thank you for the help.

After updating the kernel, when I inserted the blank disk, serpentine automatically asked me what I wanted to do with it. This is different from before. I closed serpentine and burned the disk with gnomebaker. This time, it took quite a while longer, though still at 4X. And it plays in my house player and car player both.

From now on, I will google the error messages.
From now on, I will google the error messages.
From now on, I will google the error messages.
From now on, I will google the error messages.
From now on, I will google the error messages.
From now on, I will google the error messages.
From now on, I will google the error messages.

Thank you for your help (again)
\Peace,
R-

---

### Post by RichPicker on 2007-06-05
I spoke too soon. It does not work. I get the same 'growisof' error message with Serpentine. With gnomebaker, it tells me it burned the CD successfully, and I can see where it's burned tracks in it, but all my player, including the CD that created it, tell me it's a blank disk.

How can I find out what's going wrong? How can it work yesterday, but not today? Is there a way to test the CD device itself? I am still completely lost with this.

---

### Post by RichPicker on 2007-06-05
And yes I googled the error messages from both applications, but I can not understand any of it - and none of it points in any direction to fix anything.

---

### Post by RichPicker on 2007-06-05
K3B worked just now. 

I don't think it's a problem with the driver, the burner, or the kernel. I think it's flaky software. But, what do I know. Not much.

---

