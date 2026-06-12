---
title: "Advice on partition design..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-06-09
> **pneaveill said:**
> NTFS is and has been very buggy and only slightly more secure than Fat32. Despite exceptions, Linux systems, are, typically far more secure and stable than window$ ever dreamed of being.

I had heard that Linux is more stable & secure than Windows, which are a couple of the main reasons I'm here. I thought that was a direct result of the OS, though. I didn't know the file system played a part in that.

I'm trying to discern how to partition my drives.

I would love to ditch Windows but don't think I'll be able to as I have to run a couple of Windows programs specific to my industry, though in time I may be able to migrate out of that. I use my computers for both home and work and unfortunately some of the companies I interact with require the use of Internet Explorer to access their pages. I think it must have something to do with secure pages. Firefox will work with some but not others. In some I can open Explorer in a Firefox tab, but in others I must open & use IE in stand alone mode. Bummer.

Anyway, as far as I can tell, I'll probably need to double boot and would like to set up the most efficient file system from the get go. Would something like this work?

1.  Windows operating system
2.  Windows swap file
3.  Ubuntu operating system
4.  Ubuntu swap file 
5.  Shared partition for programs and docs for Windows & Ubuntu

Am I missing anything?

Would it then be best to set up partition # 5 for ext3 and and download [IFS For Windows]("http://www.fs-driver.org/") vs setting it up as and NTFS file & downloading [NTFS-3G Read/Write Driver]("http://www.ntfs-3g.org/index.html") so that Ubuntu could read & write to that partition as well as Windows?

Could the disk(s) be encrypted and still be fully utilized by both operating systems under both scenarios?

What size(s) should I probably set for each partition?

I have an 80 G hard drive and 1 G of memory.

Hopefully I'll be able to add another 80 G IDE hard drive and have a couple of 80 G USB hard drives that are already formatted and being used by another computer using the NTFS file system. One is completely full the other is about 3/4 full. Quite a bit of that is pictures which could be burned to CDs or DVDs. I need to clean them up a bit anyway & could probably move data around and reformat those disks if need be.

Any recommendations & advice would be appreciated.

---

### Post by logicalmind on 2007-06-09
First the windows swap file usually goes onto the same drive as the windows system directory. You would only put it on it's own partition if that partition was physically on another disk.(otherwise you gain no I/O benefit by it being on a different partition but on the same drive).

As for partition 5, unless your programs are OS independent, like Java apps, you will not share programs between windows and ubuntu. So I assume you mean sharing data and not programs. There is more effort in making linux read windows partitions than the reverse(after all windows has a major lead in market share). So if I were you I would make partition 5 FAT32 or NTFS and mount it r/w in linux to solve your problem.

You aren't going to be able to find an encrypted file system that is r/w between linux and windows. Your best bet is to do encryption on a file level. In windows you can use pgp, and in linux use gpg. As long as both share the same public/private keypair you can read the files in both OS.

---

### Post by ccfjeff on 2007-06-09
> **logicalmind said:**
> First the windows swap file usually goes onto the same drive as the windows system directory. You would only put it on it's own partition if that partition was physically on another disk.(otherwise you gain no I/O benefit by it being on a different partition but on the same drive).

OK, thanks for the info!
> 
As for partition 5, unless your programs are OS independent, like Java apps, you will not share programs between windows and ubuntu. So I assume you mean sharing data and not programs. There is more effort in making linux read windows partitions than the reverse(after all windows has a major lead in market share). So if I were you I would make partition 5 FAT32 or NTFS and mount it r/w in linux to solve your problem.

I don't quite understand this part.  If it is more difficult getting Linux to read NTFS or FAT32 file structures than it is to get Windows to read Linux file systems wouldn't that mean it would be easier to set the shared partition up in a Linux file structure?

BTW, is the "more effort" pertain to the original setup, or does it take more time/system resources for Linux to read/write the Windows partitions?  Is the data pretty secure in either setup?  ie.  Is it more likely for the data likely to be accidentally corrupted in one scenario than another?

> You aren't going to be able to find an encrypted file system that is r/w between linux and windows. Your best bet is to do encryption on a file level. In windows you can use pgp, and in linux use gpg. As long as both share the same public/private keypair you can read the files in both OS.

Thank you very much for the info & advice!  You may have saved me many headaches.

---

### Post by bulaohu on 2007-06-09
Two out-of-the-square ideas, may not suit your situation perfectly but I reckon worth considering,

1. Store your docs online in Google Docs. With broadband Internet connection, Internet is the unlimited extension to your local file system.

2. It's more and more popular for people to run one OS, then VM software, then another OS. This way you can have two OSes running at the same time, and you don't need to reboot the machine to switch. Personally I believe 5 years later no one would even talk about dual-booting anymore.

---

### Post by ccfjeff on 2007-06-09
> **bulaohu said:**
> Two out-of-the-square ideas, may not suit your situation perfectly but I reckon worth considering,

1. Store your docs online in Google Docs. With broadband Internet connection, Internet is the unlimited extension to your local file system.

Thanks for the feedback.  A couple of potential negatives with that idea, however:

1.  I'm a little concerned that Google might not be as secure as a local hard drive.  Some of the info from work is sensitive.

2.  Can you store anything on Google Docs?  It seems to me like I had tried to save a pdf file and it wouldn't work. 

>  2. It's more and more popular for people to run one OS, then VM software, then another OS. This way you can have two OSes running at the same time, and you don't need to reboot the machine to switch. Personally I believe 5 years later no one would even talk about dual-booting anymore.

That actually would be an ideal situation for me.  A big problem I have is that I don't have disks for the Windows OS.  One computer I had purchased online from PC Mall was an HP factory refurb and it came with no disks -- all of the software was pre-installed.  As a matter of fact that has been a major headache for me as the hard drive crashed and I couldn't recover anything and had no recovery disk or backup.  Yeah, not too smart, but that's what happened.  A computer guru reinstalled the OS for me but his company went out of business and a year or so later I started getting Microsoft'$ "Genuine Advantage" virus popups and assorted irritating garbage delaying startup etc.

I just purchased another used computer off of Craig's list, but once again I got no CD with the OS on it.  It's running Win XP Pro, just like my other one but I don't have the CDs for either and I think that is necessary for installation of the VM software as I understand it.

Dual booting would be a nice option, but having Windows run as a Window under Linux would be the ideal by far.

---

### Post by logicalmind on 2007-06-09
> **ccfjeff said:**
> OK, thanks for the info!


I don't quite understand this part.  If it is more difficult getting Linux to read NTFS or FAT32 file structures than it is to get Windows to read Linux file systems wouldn't that mean it would be easier to set the shared partition up in a Linux file structure?

BTW, is the "more effort" pertain to the original setup, or does it take more time/system resources for Linux to read/write the Windows partitions?  Is the data pretty secure in either setup?  ie.  Is it more likely for the data likely to be accidentally corrupted in one scenario than another?



Thank you very much for the info & advice!  You may have saved me many headaches.

Sorry, I wasn't clear on my definition of effort. I meant there is more development effort involved in making windows partitions work with linux. Meaning it will likely work better for you. 

As for corruption, I haven't used the ntfs r/w module in years. When I last used it it was experimental, but I had no problems with it. Maybe someone is using it now and can let us know how well it works.

As for security, that quote you started with is a bit misleading. It is hard to talk about security in vague terms since security has many levels. Comparing extfs and ntfs in terms of security it depends on what you're trying to secure against. Physically, if you give  me either an extfs or ntfs drive I can mount it in my machine and read either of them just as easily. The difference lies in whether another user on your machine under another account could access your data. This kind of access control is easier to use in extfs. Realize that if someone is using your account on your machine they can access the data on these drives as easily as you can. 

If you tell me the kind of security threat you want to protect against I may be able to give you more advice.

---

### Post by bodhi.zazen on 2007-06-09
Here is some general information you might find helpful :

[Basic Partitioning info](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by ccfjeff on 2007-06-10
> **logicalmind said:**
> Sorry, I wasn't clear on my definition of effort. I meant there is more development effort involved in making windows partitions work with linux. Meaning it will likely work better for you. 

Thanks for the clarification.  That cleared it up for me.

> As for security, that quote you started with is a bit misleading. It is hard to talk about security in vague terms since security has many levels. Comparing extfs and ntfs in terms of security it depends on what you're trying to secure against. Physically, if you give  me either an extfs or ntfs drive I can mount it in my machine and read either of them just as easily. The difference lies in whether another user on your machine under another account could access your data. This kind of access control is easier to use in extfs. Realize that if someone is using your account on your machine they can access the data on these drives as easily as you can. 

If you tell me the kind of security threat you want to protect against I may be able to give you more advice.

Thanks for the feedback.  I wasn't specific enough there.  My primary concern is really from external threats such as trojans or someone gaining access through website shenanigans, etc.  I'm also leery of key loggers or interceptions of data transmissions over the internet, though that is a different issue than file systems.

I'm a little one man office at the moment so I'm not worried too much about other users on a network, though I do hope to set up a small network, including wireless for my wife and children to be able to use the internet and perhaps for us to do a little file sharing here and there.

I do interact, though with insurance companies and license bureaus, some of which require the use of Internet Explorer as far as I can tell.  Some of that is over secure web pages, but I also must put some of them into Internet Explorer's "trusted zone" for the pages to work correctly.  Many also use Java.  I have also had technical issues and occasionally their techs will want to get remote access to my computer to troubleshoot the problem.  Sometimes I have eventually figured out that I had to put other remote domains into IE's "trusted zone".  Some pages use java to throw you over to another site that they apparently use but that has a different domain name.

I would like to set things up to where it would be difficult if not impossible for someone to remotely get into customer files or data without my knowledge or permission, particularly a rogue employee or company or some malicious website.  

Would encryption of the files/partitions be a way to harden the system from such attacks?  Would it make it impossible or at least very difficult for a trojan to be able to transmit data back to an outsider?  Would it perhaps even keep someone from being able to read it if they stole the computer and could put the hard drive in another computer?

Thanks again for any help and insights.

---

### Post by ccfjeff on 2007-06-10
> **bodhi.zazen said:**
> Here is some general information you might find helpful :

[Basic Partitioning info]("http://ubuntuforums.org/showthread.php?&t=282018")

That looks like an excellent reference.  I haven't had a chance to go through it in detail yet, though I most certainly will.  Thank you very much!  It looks like you've written at least a couple of good references.  If you keep this up you could probably compile them into a book or a computer course.

---

### Post by knightnet on 2007-06-15
Hi, I use both and would recommend something like:

1st Primary partition = NTFS
2nd Primary partition = ext3 - mounted as "/" (the linux root partition under which everything else fits)
3rd partition = swap - 1G max, you can probably get away with .5G but don't try to suspend!

How you split the sizes of your partitions depends on what you are keeping on them. I normally give 40G to my Linux partitions but I have a seperate 250G linux data partition and Windows on seperate hard drives altogether (I use 4 disks plus a network attached storage device with another 250G!). Windows apps tend to need more space but the data is the important thing. I use mapping software under Windows the maps and various video projects take most of my space - the latter now mainly happens under Linux.

This keeps things simple! no messing around with too many partitions. As you say, both XP and Linux can access each others partitions (just about!). If you create too many partitions you will inevitably run out of space on at least one of them and then muck around for ages trying to sort it all out - trust me on this, I've done it too many times myself!

Things get even easier if you can dedicate whole drives to Windows at least so you might want to consider that too.

As for having to run Windows apps, I sympathise as I am in the same situation - though you can now run a lot under WINE - including IE.

For the encrypted file system, I recommend using TRUECRYPT which runs fine on both Windows and Linux. You can dedicate an actual partition to this if you want (I use a file as a virtual partition that I keep on a USB stick and back up to several places). The truecrypt volume will use FAT format which is easily accessible from both OS's.

One final thing is that you just about have enough memory to run virtual machines so you might consider running VirtualBox or VMware Player under Linux when you need a Windows app.

Regards. J.

---

### Post by indytim on 2007-06-15
One thing I would add to the mix.  If you're planning on adding a new HD, you may want to opt for something bigger than 80G.  Prices have really plummeted on HDs recently.  Since you're in the U.S. you could take advantage of some of the bigger on-line HW supply houses.  If you go that route, you could designate your existing HD for Windows ops and your Linux ops.  Use the second HD for data storage partitioned accordingly.

Just a thought,

IndyTim

---

### Post by ccfjeff on 2007-06-15
Nevermind.  Dell apparently doesn't have a bay for a second hard drive on their Dimension 1100.

Sorry about that.

---

### Post by ccfjeff on 2007-06-15
Thank you for the response & advice!

> **knightnet said:**
> Hi, I use both and would recommend something like:

1st Primary partition = NTFS
2nd Primary partition = ext3 - mounted as "/" (the linux root partition under which everything else fits)
3rd partition = swap - 1G max, you can probably get away with .5G but don't try to suspend!

What is "suspend"?

>  How you split the sizes of your partitions depends on what you are keeping on them. ... Windows apps tend to need more space but the data is the important thing. ...

This keeps things simple! no messing around with too many partitions. As you say, both XP and Linux can access each others partitions (just about!). If you create too many partitions you will inevitably run out of space on at least one of them and then muck around for ages trying to sort it all out - trust me on this, I've done it too many times myself!

Is much/anything lost in keeping Windows apps on a Linux partition or Linux apps on Windows partitions?  If not, it would seem like one could set up the partitions to give just enough room for the respective OSes and swap files and then put everything else, both programs and data, on one giant partition.  That would seem to allow the most efficient use of space if it didn't bring too much system overhead for the non-native program to use it that way all of the time.
> 
Things get even easier if you can dedicate whole drives to Windows at least so you might want to consider that too.

I think that's probably what I'll try to do if I can figure out how to add that second drive without a drive bay in the chassis (at least that I can see).

>  As for having to run Windows apps, I sympathise as I am in the same situation - though you can now run a lot under WINE - including IE.

One problem for me is that some of my apps are not mainstream at all.  They are industry specific and can change rather rapidly.

One thing that I don't quite understand is the compiling and binaries and things.  I've read bits and pieces here and there but it's over my head at this point.  Can one take any Windows program, compile it into some sort of binary and then translate it into a program that will run in Linux?  I'm guessing no, or most of these conversations about incompatibilities wouldn't be occurring, but that's the mental picture I'm getting at the moment.

> For the encrypted file system, I recommend using [TRUECRYPT]("http://www.truecrypt.org/") which runs fine on both Windows and Linux. You can dedicate an actual partition to this if you want (I use a file as a virtual partition that I keep on a USB stick and back up to several places). The truecrypt volume will use FAT format which is easily accessible from both OS's.

Thank you for that valuable piece of information.  That will add another wrinkle to how to partition the drive(s), though, if it is FAT32 only.

>  One final thing is that you just about have enough memory to run virtual machines so you might consider running VirtualBox or VMware Player under Linux when you need a Windows app.

That sounds like an ideal and I'm just starting to research it a little bit.  One big hurdle for me there is that neither of my newer computers has a Windows install disk.  They both came with Windows pre-installed and no media, not even the OEM.  As I understand things, however, even the OEM disks wouldn't work for creating a virtual Windows machine.

I'm thinking I might be able to use a virtual Ubuntu machine within Windows, though that  probably defeats some of the advantages of running Linux vs Windows.  If 1 GB is "almost enough", how much do you think would be sufficient?

I added 256 MB of Ram to the 128 MB that came with my other machine and yet it still bogs down a lot at times.  I don't know if I'm ADD or what but I often seem to end up with a number of different programs and windows open.  Firefox seems to keep growing in memory use the longer it is open as well, particularly if any windows were .pdf files.  Acrobat never seems to let go of any memory even after you close the windows.

I had hoped to try my hand at a little bit of video editing, but it sounds like that uses up a ton of resources.  From the sounds of things I wouldn't have anywhere near the disk space if your usage is any indication of things, and I imagine I would be borderline at best with Ram even if I weren't running in Virtual Machine mode.

>  Regards. J.

Thanks, I do appreciate the help.

---

### Post by knightnet on 2007-06-18
> **ccfjeff said:**
> Thank you for the response & advice!
What is "suspend"?

Suspend to disk. For laptops mainly though it should work with desktops too. Under Windows, a file is created to hold the contents of RAM. Under Linux, the RAM is written out to the SWAP space so it needs to be as big as your RAM (more or less). Not an issue if you don't use this.
> **ccfjeff said:**
> 
Is much/anything lost in keeping Windows apps on a Linux partition or Linux apps on Windows partitions?  If not, it would seem like one could set up the partitions to give just enough room for the respective OSes and swap files and then put everything else, both programs and data, on one giant partition.  That would seem to allow the most efficient use of space if it didn't bring too much system overhead for the non-native program to use it that way all of the time.

It's not recommended. Windows has only limited handling of Linux partition types and visa versa. Only FAT is well supported across both but even then, Linux ACLs are not supported.
> **ccfjeff said:**
> 
 I think that's probably what I'll try to do if I can figure out how to add that second drive without a drive bay in the chassis (at least that I can see).
 
Two drives is certainly best and easiest.
> **ccfjeff said:**
> 
 One problem for me is that some of my apps are not mainstream at all.  They are industry specific and can change rather rapidly.

One thing that I don't quite understand is the compiling and binaries and things.  I've read bits and pieces here and there but it's over my head at this point.  Can one take any Windows program, compile it into some sort of binary and then translate it into a program that will run in Linux?  I'm guessing no, or most of these conversations about incompatibilities wouldn't be occurring, but that's the mental picture I'm getting at the moment.
 
I'm afraid not - well not normally anyway. There are a few applications that you could do this with.
Thankfully, Ubuntu has one of the widest levels of support with a vast library of pre-compiled applications so it is very rare that you should need to get involved with this any more. When you do, there are normally fairly easy to follow instructions.
To run Windows applications under Wine, you don't need to recompile, just go through an "installation" using the Wine application provided.
> **ccfjeff said:**
> 
  Thank you for that valuable piece of information.  That will add another wrinkle to how to partition the drive(s), though, if it is FAT32 only.
 
Linux fully supports FAT so it isn't a problem.
> **ccfjeff said:**
> 
  That sounds like an ideal and I'm just starting to research it a little bit.  One big hurdle for me there is that neither of my newer computers has a Windows install disk.  They both came with Windows pre-installed and no media, not even the OEM.  As I understand things, however, even the OEM disks wouldn't work for creating a virtual Windows machine.
 
Hmm, yes that could be an issue.
> **ccfjeff said:**
> 
  I'm thinking I might be able to use a virtual Ubuntu machine within Windows, though that  probably defeats some of the advantages of running Linux vs Windows.  If 1 GB is "almost enough", how much do you think would be sufficient?
 
Ubuntu under Windows is good! At least until you can get a full copy of Windows anyway.
The problem with "only" 1GB is that running Windows needs LOTS of memory just to run Windows so when you are running Windows and Linux together and then applications on top, you can imagine that you need a lot of memory unless you like looking at wait cursors. On the other hand, 32bit OS's can't support more than 4GB of RAM (it's actually slightly less due to the way the memory is mapped). 2GB though comes at a reasonable price and is probably enough for most people - get as much as you can afford though.
> **ccfjeff said:**
> 
  I added 256 MB of Ram to the 128 MB that came with my other machine and yet it still bogs down a lot at times.  I don't know if I'm ADD or what but I often seem to end up with a number of different programs and windows open.  Firefox seems to keep growing in memory use the longer it is open as well, particularly if any windows were .pdf files.  Acrobat never seems to let go of any memory even after you close the windows.
 
256MB is absolutely minimal for running any of the mainstream current OS's. Under Linux, you would find that using something like Xubuntu would be a lot faster (it uses Xfce instead of KDE or Gnome) but at the sacrifice of some familiarity and features. XP with less than 512MB of RAM is SLOOOOW unless you restrict yourself to a single application running at a time. Vista needs at least 512MB just to run!
Firefox can easily grow to over 200MB of RAM, keeping the add-in's to a minimal helps a lot. Opening a PDF file opens the bloated Acrobat Reader as well as Firefox; both are probably using in excess of 100MB each! Try getting the latest Acrobat though, this seems faster to me.
> **ccfjeff said:**
> 
  I had hoped to try my hand at a little bit of video editing, but it sounds like that uses up a ton of resources.  From the sounds of things I wouldn't have anywhere near the disk space if your usage is any indication of things, and I imagine I would be borderline at best with Ram even if I weren't running in Virtual Machine mode.
 
With video, don't even think of working with less than 512MB of RAM under XP or Linux - 1GB with Vista. The more you have, the better your experience will be.
Also it does take a ton of disk space too. So your 80GB disk split several ways will only be able to store a tiny amount.
So with what you have, you could run Linux fine though would still benefit from extra RAM. To run both OS's, you really need more memory and more disk space.
> **ccfjeff said:**
> 
  Thanks, I do appreciate the help.

No problem!

Regards,

---

### Post by ccfjeff on 2007-06-18
Thanks again for the advice and feedback, knightnet!

I found a Dell manual for the Dimension on their website, thankfully.  It looks like 2 GB Ram is the max.  Unfortunately, it looks like I'd also have to pull the memory already installed and buy 2 1 GB sticks to upgrade.

I also found out that it only comes with one hard drive bay so I would probably need to use an external USB drive to upgrade there.  As you say the prices look pretty reasonable.  I wonder if that would be much slower than an internal ATA drive.

> **knightnet said:**
> [quote=ccfjeff;2851030]Is much/anything lost in keeping Windows apps on a Linux partition or Linux apps on Windows partitions? If not, it would seem like one could set up the partitions to give just enough room for the respective OSes and swap files and then put everything else, both programs and data, on one giant partition. That would seem to allow the most efficient use of space if it didn't bring too much system overhead for the non-native program to use it that way all of the time.
It's not recommended. Windows has only limited handling of Linux partition types and visa versa. Only FAT is well supported across both but even then, Linux ACLs are not supported.[/quote]

So would that mean for dual booting purposes, with 1 drive I should consider a set up like?:

1.  1 large Fat32 Windows partition which could also hold Linux data
2.  ext3 partition for Linux OS & programs (~40GB)
3.  Linux swap file (1 GB)

If I didn't set it up for dual boot, but rather set up a Ubuntu VM to run within Windows I wouldn't even need to worry about partitioning the HD?  The file would just expand or contract depending upon what was in it?

> **knightnet said:**
> So with what you have, you could run Linux fine though would still benefit from extra RAM. To run both OS's, you really need more memory and more disk space.

I guess I'll need to set it up as a dual boot for now.  Even though the additional memory and hard drive space have come down a lot and look very attractive at the moment, I know my wife will really squawk about the upgrades costing more than the computer did.  Especially since I sold her on it being bigger and faster than my older one.  Oh well.

At least being able to run Linux and some of the associated programs would be very nice.  The dual boot thing would make it harder to run throughout the day, though, as it wouldn't be ideal to have a client or company partner on the line and have to reboot my machine to run that occasional Windows app.

I certainly do appreciate the time and help you have given me!  It's much easier to set things up right the first time than to try and rearrange things later.

---

### Post by bodhi.zazen on 2007-06-18
Sorry if I did not read everything , those posts are long.

If I understand the gist of what you want, +1 to more ram.

Then run VMWare. Run Ubuntu as a host, vista as a guest, disable internet connections on vista (connect to host only) :)

---

### Post by ccfjeff on 2007-06-18
> **bodhi.zazen said:**
> Sorry if I did not read everything , those posts are long.

Sorry about that.  I didn't have time to write a shorter post.  ;)

> **bodhi.zazen said:**
>  If I understand the gist of what you want, +1 to more ram.

Then run VMWare. Run Ubuntu as a host, vista as a guest, disable internet connections on vista (connect to host only) :)

Actually, I have XP Pro installed on both computers.  I don't have install disks for either one, however.  Could I still run XP as a guest without the install disks?  I thought I read somewhere that you can't do so even if you have the OEM disks (which I don't have anyway).  One was a HP factory refurb.  The other was purchased use on Craig's List.

Thanks for any info/advice/recommendations.

---

### Post by bodhi.zazen on 2007-06-18
> **ccfjeff said:**
> Sorry about that.  I didn't have time to write a shorter post.  ;)

hahahahahaha

> Actually, I have XP Pro installed on both computers.  I don't have install disks for either one, however.  Could I still run XP as a guest without the install disks?  I thought I read somewhere that you can't do so even if you have the OEM disks (which I don't have anyway).  One was a HP factory refurb.  The other was purchased use on Craig's List.

Thanks for any info/advice/recommendations.

Yes you can. It is called VMConverter :

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

And if you have problems, take a peek here :

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by ccfjeff on 2007-06-18
> **bodhi.zazen said:**
> > Actually, I have XP Pro installed on both computers. I don't have install disks for either one, however. Could I still run XP as a guest without the install disks? I thought I read somewhere that you can't do so even if you have the OEM disks (which I don't have anyway). One was a HP factory refurb. The other was purchased use on Craig's List.

Thanks for any info/advice/recommendations.Yes you can. It is called VMConverter :

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

And if you have problems, take a peek here :

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Thank you once again!  If I can figure this out I will be in heaven.  Or at least very very happy.  :p

---

### Post by knightnet on 2007-06-20
> 
So would that mean for dual booting purposes, with 1 drive I should consider a set up like?:

1.  1 large Fat32 Windows partition which could also hold Linux data
2.  ext3 partition for Linux OS & programs (~40GB)
3.  Linux swap file (1 GB)
I'd try making the Linux OS partition smaller if you are going to keep most stuff on the FAT disk - otherwise you might run out of space on the FAT disk fairly quickly. 20G should be plenty to get going on Linux.

One additional tip: Don't forget that Linux partitions support "links". These are MUCH more powerful that the thing of the same name under windows. By learing the "ln" command, you can create transparent links to your FAT partition. So you can create a single Linux partition (that gets mounted as "/", the root folder). Under /home/yourusername you can create LINKS to Documents, Pictures, etc. on the FAT disk. Just delete the folders of the same name that the OS install will create and then from the command line (as yourusername, not root):
```
ln -s /home/yourusername/Documents /mnt/myfatpartition/My Documents
```Of course, you'll need to amend that to your actual installation.

Now, you have easy access to your documents, etc and dont have to worry even if you manage to make a mess of your Linux partition (not uncommon when you are learning Linux!).

Regards,

---

### Post by ccfjeff on 2007-06-20
Thank you very much once again!

My "new" computer already has WinXP on it, so I assume it is currently formatted as one giant NTFS partition for the whole drive.  I don't have an install disk for WinXP, however.  

Would I need to have a separate NTFS partition then for the WinXP OS & a little room for it's swapfile or virtual memory or whatever?

Would it be advisable to shrink the current partition and add ~ a 20G EXT3 partition for Ubuntu and another 1G EXT3 partition for Ubuntu's swapfile, and use the rest as a FAT32 partition to be shared by Windows & Ubuntu?  If so, what size would be reasonable for the WinXP NTFS partition?

Does GParted format the partitions it makes or is that a separate step &/or program?

That's an interesting website you have, by the way.  Of course, that may be more interesting to me because I am also wanting to learn more about web design and mySQL (or OO's Base) for [my business]("http://www.buchholzins.com/") and also [Christian issues]("http://www.buchholzins.com/cir/") (though, surprisingly to me, I realize some people don't consider Catholics to be Christians).  Like many people, I am also actively exploring security issues for both business and family.  So [your site]("http://www.knightnet.org.uk/") looks like it will be a good resource.  Thanks for that as well.

---

### Post by knightnet on 2007-06-29
Hi, sorry I've been caught up with the floods in Sheffield and work so things have been a little hectic :(

> **ccfjeff said:**
> Thank you very much once again!

My "new" computer already has WinXP on it, so I assume it is currently formatted as one giant NTFS partition for the whole drive.  I don't have an install disk for WinXP, however.  

Would I need to have a separate NTFS partition then for the WinXP OS & a little room for it's swapfile or virtual memory or whatever?

Would it be advisable to shrink the current partition and add ~ a 20G EXT3 partition for Ubuntu and another 1G EXT3 partition for Ubuntu's swapfile, and use the rest as a FAT32 partition to be shared by Windows & Ubuntu?  If so, what size would be reasonable for the WinXP NTFS partition?



You only need one partition for XP. It doesn't need a swap partition like Linux.
Defrag your XP partition and then shrink it but keep it at least 10-20GB depending on how many applications you have and how much data - it is difficult to give a definitive answer I'm afraid. If Windows is your primary OS, you want to keep as much as possible - remember that Windows will typically need more space than Linux so if you are struggling, you could reduce that 20GB Linux partition. If you are not doing Video or mega amounts of music storage, your data sizes will probably be <10GB anyway and a straight forwards Linux installation (without too many applications) will probably also fit in 10GB as well.

Hope that helps rather than confuses! :)

> **ccfjeff said:**
> 
Does GParted format the partitions it makes or is that a separate step &/or program?


Yes it can do but your Linux installation will probably want to format the Linux ones anyway so it doesn't really matter either way.

By the way, I've found that gparted is not really that good and it seems monumentally slow to me! You might want to try the Live CD version of PSLinuxOS or a Live CD version of SUSE. These have proprietary partition editors that you may find easier to use (and a lot faster!). They also let to do things like set the partition name which saves a lot of confusion later on.

> **ccfjeff said:**
> 
That's an interesting website you have, by the way.  Of course, that may be more interesting to me because I am also wanting to learn more about web design and mySQL (or OO's Base) for [my business]("http://www.buchholzins.com/") and also [Christian issues]("http://www.buchholzins.com/cir/") (though, surprisingly to me, I realize some people don't consider Catholics to be Christians).  Like many people, I am also actively exploring security issues for both business and family.  So [your site]("http://www.knightnet.org.uk/") looks like it will be a good resource.  Thanks for that as well.

Thanks! Sadly I've not had time to do anything with it for a long time (between work and family!)

I am actually planning a new version of the web site and I am migrating across to a new host (dreamhost.com in the US) but I've only had the chance to do a bit of playing - mainly with migrating email as the new host has a lot more control. Of course, I've also decided to move to Linux at the same time so I can only really blame myself for not having enough time!

So some of the information on the site is a bit dated now - but feel totally free to contact me through the contact form on the web site, I'm happy to chat. Web programming is frustrating but fun and it has been very useful for me professionally. A typical day for me now involves sending data back and forth between regular expressions, Excel, MySQL and PHP in an effort to make sense of it!

Regards,

---

