---
title: "Getting files from a mac HD in Ubuntu."
date: 2012-01-06
forum: Apple Hardware Users
---

### Post by forevermurphys on 2012-01-06
Funny I came to the forum to ask about this and there was a thread on the first page addressing it. 
This thread:
[http://ubuntuforums.org/showthread.php?t=852144](http://ubuntuforums.org/showthread.php?t=852144)


Was having the same permission problem trying to get music and photo files from a clone of my old emac on an external drive.

I tried the Sudo Nautilus and was able to successfully transfer my music files to my ubuntu machine, buuuut... said transferred music files still have a little lock icon on them. They play, but I don't have ownership.. :-/

Can I fix this? I saw something in that other thread about changing my ubuntu username/password to match the mac one. Can I do that? If so how? (I am a linux dolt, so be detailed) and if not other suggestions?:-({|=

---

### Post by coffeecat on 2012-01-06
The Mac files will still have the UID of your old Mac account (possibly 99) **or** will now be owned by root. Your UID in Ubuntu will (probably) be 1000. Hence the ownership problem.

Assuming all the files are in your Music folder, this command will change the ownership to your Ubuntu account:

```
sudo chown -R yourusername: ~/Music/* 
```

That will also ensure that everything in the Music folder will be owned by your account - all sub-folders and contents - but since anything else that you had previously stored there will already be owned by yourself, that won't matter. Substitute your account name for "yourusername" and don't forget the trailing colon after yourusername - this ensures that all files are placed in your default group.

If your Mac music files are in another folder and you need help with the chown command, post back.

---

### Post by forevermurphys on 2012-01-07
Thanks, that worked perfectly. 
Same command to do the same with the photos when I transfer them? (changing the folder to photos obviously.)

---

### Post by coffeecat on 2012-01-07
Yes, same command. Simply change the name of the folder whose contents you need to change.

---

### Post by fuzzywobs on 2012-03-23
I have the exact same problem, only this solution

sudo chown -R yourusername: ~/Music/*
does not seem to work for me. I get the message

chown: invalid spec: 'fuzzywobs:' .... Any thoughts?

---

### Post by coffeecat on 2012-03-23
> **fuzzywobs said:**
> 
chown: invalid spec: 'fuzzywobs:' .... Any thoughts?

Yes - "fuzzywobs" is not a user account name in the system you are running the chown command in. Post the output of these two terminal commands:

```
users
id
```

---

### Post by fuzzywobs on 2012-03-23
[IMG]http://i.imgur.com/B7pbb.png[/IMG]

I appreciate all the help I can get!

---

### Post by coffeecat on 2012-03-23
You are running from the live CD or live USB Ubuntu session which will not know anything about your fuzzywobs account on your permanent installation - that's if you have a permanent Ubuntu installation.

Tell us exactly what you are doing and what you are trying to achieve, and then we will be able to help.

---

### Post by fuzzywobs on 2012-03-23
Bearing in mind that ive never used Ubuntu before (although I reckon I will adopt it once this issue is resolved)

To keep this simple:

1. Macbook was dropped and seeminly damaged. Now when booting up, i hear  the chime, loading screen, background image appears, and I can move my  cursor, while the system tries to boot up.... and thats it. Just moving  my cursor around an image. No Operating system or anything.

2. Tried to Disk repair with OSX install CD and Disk Utility. Tells me its too damaged and I must format and reinstall.

3. Boot the laptop with Ubuntu CD. I see all my folders from my Mac, I can  only copy and backup one folder that is enabled for sharing. All other  ones I get  "The folder contents could not be displayed."

4. I type gksudo nautilus into Terminal and now i can see all files from my Mac harddrive but get 

"There was an error copying the file into /media/HDDRIVE2GO."
and
"Error opening file: Permission denied"

so I am unable to back up these files/folders.

5. Any thoughts on how I can salvage these files?

PS Yes, I am an Ubuntu noob :/

---

### Post by coffeecat on 2012-03-23
The problem may be is that the Apple HFS+ filesystem on the drive from the damaged Macbook is the journalled version, which Ubuntu/Linux can mount read-only but not write to. Which means that Ubuntu cannot chmod any of the permissions on the HFS+ drive. The usual way of getting around that is with a gksu nautilus file browser which gives you root privileges -  which is what you are trying. Unfortunately, MacOS sometimes sets somewhat restrictive permissions in your personal files, such that you get the error you see when trying to copy them, even with a root nautilus. I've seen this myself. Very frustrating.

However, you *should* be able to copy at least some of the files. Do you get that "Error opening file: Permission denied" message with all files or just some of them? If with all, I would suspect a deeper problem, perhaps the drive is really too damaged.

At the moment, the only other solution I can think of is to use another Mac to mount the drive and (hopefully) copy the files. Can you do that with the Mac install DVD? It's been a long time since I used one and I can't remember what utilities you have apart from Disk Utility and the installer on it.

If I think of anything else, I'll post back. In the meantime, do you know what filesystem is on your HDDRIVE2GO drive? I doubt that is the problem but it would be useful to know for completeness sake.

---

### Post by fuzzywobs on 2012-03-23
I think the harddrive is in OK shape, seeing as I can access all the files using gksu nautilus, and am just left not able to save them due to read only status. The folders with the X on it are the ones that I cannot access.

[IMG]http://i.imgur.com/U2dL3.png[/IMG]

The folder i can access and copy with gksu nautilus is one i made and put there myself, and is not one of the default ones. With gksu nautilus I can see all the files(at least all the ones i tried)  and just get this message when trying to save them 

[IMG]http://i.imgur.com/iGiRi.png[/IMG]

I reckon the 
	sudo chown -R yourusername: ~/Music/*
could easily be the solution, and it's just that I am doing it wrong seeing as I am unfamiliar with Ubuntu/terminal. This is what I have tried... 

[IMG]http://i.imgur.com/tSHuC.png[/IMG]


(Notice the X's on the folders are now gone)

---

### Post by coffeecat on 2012-03-23
First thing. You are confusing the files in your Ubuntu live session home folder (there are no files in the Documents folder - hence the error message) with the files in your Mac home folder. Be that as it may, if you were able to create the Kayleigh folder in your Mac home folder with a gksu nautilus window, then the HFS+ filesystem on your Mac drive is either non-journalled (which is very unexpected) or truly very damaged. Try this from the Ubuntu live session:

```
sudo chmod 777 -R /media/Mac\ Snow\ Leopard/Users/fuzzywobs/*
```

(There is one space after each of the backslashes in that command.) What happens? Are you then able to copy the files?

---

### Post by fuzzywobs on 2012-03-23
I should have probably been more specific, the Kayleigh folder is one that I made months ago and had put it in the same folder as Movies, Music etc when I had my Mac working. It is one of the only ones available to copy now that the Mac is broken.

I tried that line you gave and specified the documents folder, and it gave me a massive list of this: 

[IMG]http://i.imgur.com/e5hp1.png[/IMG]

I then tried to copy the files both before and after having used  gksu nautilusand neither seem to have worked. After I type in 

sudo chmod 777 -R /media/Mac\ Snow\ Leopard/Users/fuzzywobs/*
Is there any particular way I should try and copy them, or whats the deal?

PS Thank you again for taking the time for checking this. Its very frustrating having access to all my files, and just not be able to back them up.

---

### Post by fuzzywobs on 2012-03-23
I also tried: 
[IMG]http://i.imgur.com/y1qXL.png[/IMG]

---

### Post by coffeecat on 2012-03-24
@fuzzywobs, apologies - I missed something in the screenshots you posted last night in your post #11 which explains why you were getting the 'x' symbols on the folders in your Mac drive at one time and not another. It might also explain why you are having trouble copying your files. Have a look at those screenshots again. The nautilus one with the 'x' symbols on the folders is a non-privileged one - owner 'ubuntu'. The account 'ubuntu' is the live session non-privileged account. The nautilus without the 'x' symbols is one with root privileges opened with 'gksu nautilus'.

I believe - I'm hoping - that the following will work. Try this.

Boot up the live Ubuntu CD and plug your Mac drive in. **Now close the nautilus window that opens showing you the contents of your Mac drive.** You don't need it and it only serves to confuse. This is possibly where you are going wrong. Next - open a root nautilus with 'gksu nautilus'. In fact, do this instead:

```
gksu nautilus /media
```

It's a bit more elegant because you don't have to navigate so much around the Ubuntu live filesystem. It will open in the /media folder and you will see the 'Mac Snow Leopard' folder. Open the Snow Leopard folder, then the Users folder, and you will see your Mac files.

**Now** and only now, plug your 'HDDRIVE2GO' external drive in. A non-privileged nautilus window showing the HDDRIVE2GO drive will open - leave it open. **Do not try to copy any files to your Ubuntu live desktop. ** All files in your live desktop are held in RAM and you may run out of memory and, besides, you may run into permissions issues if you copy to the live desktop. I am hoping that your HDDRIVE2GO drive is formatted FAT32 or NTFS - you didn't say - which are Microsoft filesystems and which do not support the system of permissions that Ubuntu and MacOS use. In this instance this is a bonus because by using a Microsoft filesystem you neatly sidestep permissions/ownerships problems.

Now simply copy your files by drag and drop from the nautilus window with the Mac files to the nautilus window showing HDDRIVE2GO. If you follow these steps correctly and if HDDRIVE2GO is FAT/NTFS, this will work.

Let us know how you get on. If everything copies OK, then I'll explain some of the other points that were confusing you. For example, your Mac drive is read-only in Ubuntu as I expected - your latest posts show this.

---

### Post by fuzzywobs on 2012-03-24
Right... I tried this and it seemed to give same results as before, so i restarted the laptop and booted up the Ubuntu live CD from scratch. 

I then followed your instructions exactly, and got a different message when i tried 

gksu nautilus /media
[IMG]http://i.imgur.com/gtHGK.png[/IMG]

But the nautilus window does open showing this;

[IMG]http://i.imgur.com/dQ14G.png[/IMG]

showing a lock instead of an X on the Mac Snow Leopard hard drive. 

I can then navigate and view all the files and folders i need to back up, but only in read only and cannot copy and back up the files...

---

### Post by coffeecat on 2012-03-24
If you can read them you should be able to copy them. Are you trying to copy them to an external drive formatted FAT32 or NTFS?

EDIT: - ignore the error messages you get in the terminal when you run "gksu nautilus". They signify the square root of not much at all.

---

### Post by fuzzywobs on 2012-03-24
I just formatted my 8 gig USB to FAT (to make sure) and tried again with the same results. I can view them but not copy them:

[IMG]http://i.imgur.com/lTe8y.png[/IMG]

---

### Post by coffeecat on 2012-03-25
@fuzzywobs, sorry I didn't get back to you yesterday - long day with other things taking up my time. I'm puzzled as to why you are getting these difficulties. I'm going to run a simulation to see if there is anything else to take into account. I'll post again in a few hours.

---

### Post by coffeecat on 2012-03-25
OK, I *think* I've got to the bottom of what's going wrong for you and, if I'm right, there is only one solution which I'll come to shortly.

I used a Carbon Copy Clone backup of my entire MacMini Snow Leopard installation to test this out. The drive would boot into Snow Leopard if I were to fit it to a Mac machine so it is comparable with yours.

I plugged it into a machine running Ubuntu 11.10 from a live CD (I think you are running 11.04 - judging by your screeshots - but the difference in version won't make any practical difference.) Interestingly, I was able to drag and drop copy many of my personal files using a non-privileged nautilus window. Those folders that I was not able to copy had an 'x' icon signifying restrictive permissions and I had to use a gksu nautilus to open them - that's all expected and what you have seen. However, even with a gksu nautilus I got a permission denied on occasion when trying to copy and the reason for this was a single file with 700 permissions (very restrictive). Tbh, I was slightly surprised that a root nautilus could not copy it, but there you are.

I hinted at this possibility before because I have seen MacOS create files with restrictive permissions in an unpredictable way before.

The solution? I know of no way of getting round this that does not involve using a working MacOS. The permissions/ownership of the offending files need to be changed and for that you need write access to the drive. It is theoretically possible to force mount your Mac drive read-write in Ubuntu, but this is something that I have not done nor would I want to recommend it. Your data would be at risk, in my opinion.

If you do have access to a working Mac, post back and I'll take you through what you need to do to adjust the permissions. The quick way, even in a Mac, is with a single terminal command (!), or it can be done with the GUI.

By the way, the padlock symbols that you saw on the folders in Ubuntu simply mean that they are read-only - and that's because your HFS+ drive is mounted read-only in Ubuntu.

---

### Post by fuzzywobs on 2012-03-25
wow... thanks for looking into this in so much detail. 

A colleague of mine has a Macbook Pro so I should be able to convince him to let me borrow it for a day to help retrieve my files. Hopefully I will be able to get this off him on tuesday/wednesday.

 What is involved using this method? I've not looked into this method at all so am rather clueless. 

Thanks again!

---

### Post by coffeecat on 2012-03-25
I was making an assumption - I think unjustified - that you had removed the hard drive from the MacBook and had put it in a USB enclosure. Re-reading your posts I see that you were probably booting the MacBook with an Ubuntu CD.

If you can remove the drive and put it in a USB enclosure, so well and good. You'd simply plug the USB enclosure in and it will be automounted by your friend's MacBook after which you'd be able to browse the filesystem and copy your files. Or, if you ran into permissions problems, it would be possible to adjust the permissions in MacOS.

If you can't remove the hard drive, it is possible for one Mac to mount the drive of another if the two are connected with a firewire cable, but I can't remember whether the one mounted has to be able to boot up or not. Sorry - long time since I've done this. And, didn't Apple remove firewire from some models?

---

### Post by fuzzywobs on 2012-03-25
I have not yet removed the harddrive as I am unable to access another machine to access it from. I was hoping that I would be able to access straight off my own computer. I buy a SATA USB harddrive enclosure this week and borrow a colleagues macbook and hopefully will be able to transfer all the files.

On a side note, when i boot up the Snow leopard installation CD and try to repair the harddrive, it recommends I format and reinstall. Do you think that would work, based on the fact that the computer was damaged due to a fall?

Also, on a complete other side note, my Macbook is pretty old now, nearly 5 years old, and in the last 12-18 months, it seems to freeze/lock up pretty regularily. Its mostly when the laptop is moved, but sometime the someone would pick the laptop wildly and set it down roughly and nothing would happen, and other times someone would purposely lift it really gently and it just locks up. I thought it might be due to loose RAM (i read somewhere online) but after removing and reinserting the RAM nothing changed. Any ideas?

Eitherway, I'll keep you posted as to whether or not i can salvage my data! And again, thanks for the help. I really appreciate you taking so much time out to try and selflessly help me. You arent just an asset to the Ubuntu team, people like you are an asset to mankind!

---

### Post by coffeecat on 2012-03-26
> **fuzzywobs said:**
> 
On a side note, when i boot up the Snow leopard installation CD and try to repair the harddrive, it recommends I format and reinstall. Do you think that would work, based on the fact that the computer was damaged due to a fall?

Re-installing Snow Leopard would, of course, erase all your personal files and thus far I had been assuming that your priority was to rescue them. Whether you still have a functional machine, I don't know.

In your situation, I think I would try to retrieve my personal files by removing the drive and attaching it to another Mac, and then replace the drive and attempt a re-install of Snow Leopard to see if a fresh install solves the problem of occasional freezes.

Occasional freezes are a nightmare of all operating systems. We get threads about Ubuntu freezing unpredictably. The question is whether it is software or hardware related, and troubleshooting this is like chasing moonbeams.

Good luck!

---

### Post by fuzzywobs on 2012-03-26
Yes, my priority is getting all my personal files, but once I have everything backed up I will try and format the reinstall the current hard drive, hoping the laptop will return to normal. My guess would be that if it does, it will still have the problem of sporadic freezing which is probably a hard ware problem. If my harddrive does not work, I will buy a new hard drive and hopefully that will solve both problems! I’ll keep you posted either way…

---

### Post by fuzzywobs on 2012-03-29
Hi, I have just bought a SATA 2.5 enclosure for the harddrive and I will hooking it up to another Macbook tomorrow. I tested it out here and it works fine connecting up to my laptop by USB. 

Is there any particular way I should change the settings, other than right clicking, get info, change sharing and permission to Read and Write? I presume it will ask me to log in? Or do i do gksu nautilus equivalent?

Thanks.

---

### Post by coffeecat on 2012-03-29
If you are going to be plugging it in to a Mac, then you don't need to do anything apart from plug it in and let the system automount it. The only reason you need a gksu nautilus window in Ubuntu is because the UID in the Mac files are different from the UID of the "ubuntu" account in the live session.

If by chance the UID of your Mac files is different from the UID of the account you use in the Macbook, you *might* run into permissions issues, but let's see what happens first.

---

### Post by fuzzywobs on 2012-03-30
Hi, so I have the Harddrive plugged into a macbook. I see that the Owner of the computer im using say "John" has read and write access to the fodler, but everybody else is (its written in french) "Interdit" ie not allowed. When i click the lock to make changes it asks for "Johns" password which I input, and unlocks, but the option to change the permissions is still greyed out. 

I can manually back up whats most important documents on "Johns" computer (although id rather not, really) and Ive an 8 gig USB stick to back up essential stuff, but my ideal solution was to change permissions so that when i get home i can manually go through everything, seeing as my current external harddrive is nearly full. If I had a massive external harddrive id just back everything up. But i'm still not sure if ill have permission issues down the line...? Thoughts?

---

### Post by coffeecat on 2012-03-30
If you are backing up to a flash drive formatted FAT32, you don't have to change permissions on that because it is a Microsoft filesystem that doesn't support the Unix system of permissions that MacOS and Ubuntu.

Are there any files that you cannot transfer from your MAC drive to the flash drive using MacOS. There is a way round that but forget changing permissions on any files already transferred to the flash drive.

---

### Post by fuzzywobs on 2012-03-30
I had to format the USB when I inserted it, so it was formatted as Mac Journeled. Everything is working semi-fine. I am able to copy file directly to the new macbook or USB thumb drive. 

The only issues are 

1. that when i try to copy a large folder, it gives me an error (after a while) saying one or more of the files cannot be copied (corrupted or what not) and cancels the whole transfer, so I literally have do each folder/file separately, which is fine. On ubuntu, when this happened, a pop-up displays saying "xxxxx.jpg cannot be copied. Would you like to skip?" type of message. On Mac it seems to be all or nothing!

2. I only have an 8gig USB drive (as I would rather not back up all my files on my colleauges computer) so I was hoping I would be able to change the permissions on the folders so that when I buy another external harddrive, then id be able to back up all my files from Ubuntu, without having to do it manually thanks to the skipping of unreadable files.

I will see if 8 gig is enough to back up, seeing as I had most the photos in that (only!) folder that I was orginally able to back up, so it might be the case that 8 gig is enough (im wont be backing up movies/tvshow/music).

So the real issue is (although not completley necessary) just changing the permissions. It makes it easier for backing up stuff by 
1. Skipping the unreadable files
2. Allowing me to do so from home where i have more time and will have a bigger harddrive.

Thanks for your thoughts!

---

### Post by coffeecat on 2012-03-30
> **fuzzywobs said:**
> I had to format the USB when I inserted it, so it was formatted as Mac Journeled.

Oh dear. That may not have been the best choice. What operating system will you be reading the USB drive with when you get home? As far as I remember, you were only running Ubuntu live from the CD and do not have a permanent installation of Ubuntu.

The quickest, easiest but dirtiest way of dealing with these permissions problems is to do a recursive chmod, using MacOS, on your home folder in the drive from which you are trying to backup. From what you posted earlier, your damaged Mac drive has the label "Mac Snow Leopard", so it should be mounted on "/Volumes/Mac Snow Leopard" in MacOS. Let's check that before I give you the full chmod command. With your damaged drive plugged in, open a Mac terminal and run this command:

```
ls -l /Volumes
```

Also - double check the label your friend has given their Mac. It's the label showing under the hard drive icon top-right of the desktop. What is it?

---

### Post by fuzzywobs on 2012-03-30
I've reformatted the USB to FAT, I was saving all the files onto Johns desktop before copying them to the USB so thats not an issue. 

Johns harddrive is called Macintosh HD and my one is Mac Snow Leopard this is the line regarding the harddrive I got (rewritten as the laptop has no internet access)

drwxrwxr-t 31 "John" 1122 "date" "time" Mac Snow Leopard

I would be wary of messing up anything in Johns computer so if there are risks, ill probably avoid. I've nearly finished backing up all essential folders. There are certain folders that contain lots of folders with lots of pictures, and it is painfully tedious trying to back them up without knowing which files are corrupt! I had 3 gig of 8gig of photos transferring across when it discovered one photo it couldnt copy, so it cancelled the whole transfer... annoying!

*edit: Yes, I will be running Ubuntu straight from CD at home. So permanent permission removal would be wish number 1!

---

### Post by coffeecat on 2012-03-30
> **fuzzywobs said:**
> I was saving all the files onto Johns desktop before copying them to the USB so thats not an issue. 

Why? That just complicates things. I was going to suggest chmodding all your files on your own drive in the USB enclosure on the assumption that you would be copying them directly to the flash drive. Neither John's computer nor his system would be affected.

---

### Post by fuzzywobs on 2012-03-30
Is it possible to chmod all the files on the harddrive in the USB enclosure now on the Macbook resolving the permission issue, and then be able to then plug the harddrive into a machine running Ubuntu and copy all the files across? Or must everything be done on a Mac? 

Because If i copy everything the transfer will be interupted and cancelled anyways once it meets a corrupt file and theres a few of them seeeing as there is random files that wont work. Ubuntu allows you to skip the corrupt files, whereas Mac wont let me.

---

### Post by coffeecat on 2012-03-30
> **fuzzywobs said:**
> Is it possible to chmod all the files on the harddrive in the USB enclosure now on the Macbook resolving the permission issue, and then be able to then plug the harddrive into a machine running Ubuntu and copy all the files across? 

Well, yes indeed. The chmod would be the same as if you were doing the copying in MacOS but I appreciate your point about Ubuntu being more user-friendly for skipping corrupt files. Kudos to Ubuntu! :)

Answer the two questions I pose in post #31, the output of "ls -l /Volumes" and the name of your friend's system and then I can give you the full chmod command.

---

### Post by fuzzywobs on 2012-03-30
[IMG]http://www.imgur.com/DHLde.jpg[/IMG]

---

### Post by fuzzywobs on 2012-03-30
Heres the screen shot. John = Laurent!

---

### Post by coffeecat on 2012-03-30
Good. I wanted to be sure that there wasn't a clash between the name "Mac Snow Leopard" on your drive and your friend's drive. In fact your friend's system partition label is "Macintosh HD" but the important thing is that is is different.

With your drive plugged in and from a Mac terminal:

```
sudo chmod -R 777 /Volumes/Mac\ Snow\ Leopard/Users/fuzzywobs
```

This will change permissions of your fuzzywobs folder and all its contents to 777, which cannot be more permissive. It will make all files executable, which is not ideal, but once you've copied them to a FAT drive using Ubuntu, you'll lose all the permissions anyway. The backslashes (\) in "Mac Snow Leopard" are to escape the spaces which are always a nuisance in filename and partition names in Unix systems. Best avoided.

Be careful when you type that in. One typo can do a lot of damage when you invoke a command with "sudo" rights as you will need to do. Also - invoking sudo elevates your privileges to root and you will see something you have not yet experienced in Ubuntu, since you were running Ubuntu live from the CD. You will be prompted for the account password (make sure you are running from an administrator account - your friend John will have to supply the password), but you will not see it echoed to the screen when you type it in. This is normal, but it appears that nothing is happening. The same happens in Ubuntu when you work from a permanent installation.

That *should* make all the files completely accessible and copyable (except the damaged ones) in Ubuntu without the use of a "gksu nautilus" window. You should now be able to use the ordinary nautilus window that pops up when you plug your "Mac Snow Leopard" drive into the Ubuntu live session. Remember to copy directly to your FAT USB drive, not to the Ubuntu desktop, and be aware that the FAT filesystem supports an individual filesize maximum of 4GB. If you have any large video files, for example, this may be a problem.

I was thinking of giving you the command to change the ownership of all your files on the Mac Snow Leopard drive to the "ubuntu" account as well, but hopefully this will not be needed with the 777 permissions. Post back if you encounter problems and we'll see.

---

### Post by fuzzywobs on 2012-03-30
Right… That was a dramatic affair just there. I was racing trying to figure out how to type a back slash on a French Mac with only a few mins left of battery on my colleagues laptop… 
  Anyways, after typing that line in, I got prompted for Johns password, which i entered and then I got this: 
   
[IMG]http://www.imgur.com/6jP3G.jpg[/IMG]



  So it didn’t seem to work. I tried plugging it back into the Ubuntu running Machine and it’s the same ol’ permission issue. I think maybe at some point in the last year or 2, I must have set the permissions to “Not Allowed” or something! 
  The battery has run out and John had to leave so I’ve no more other Mac, so either way that’s all I can do till after the weekend anyways. 



At least I’ve backed up all the essential documents, bar a few photo folders I have. So thank you very much for that! I will go through the hard drive in more detail at the weekend and check if theres anything essential left to because if not I may just be better of just formatting the hard drive and start from scratch at this point, or if that fails, buy a new hard drive. Thanks for all your help though, you’ve been too helpful! Have a good weekend!

---

### Post by coffeecat on 2012-03-30
If you look closely at the terminal output, you'll see that it repeatedly says "Read-only file system". Which is why the chmod command is not working. Same as in Ubuntu - you can't chmod a filesystem mounted read-only - except that the reason for it being read-only in Ubuntu is different. But that raises a mystery - why is the filesystem read-only in MacOS? It would need a bit of investigation and I wouldn't be surprised if the filesystem itself is damaged and you may have gone as far as you can.

Good luck!

---

