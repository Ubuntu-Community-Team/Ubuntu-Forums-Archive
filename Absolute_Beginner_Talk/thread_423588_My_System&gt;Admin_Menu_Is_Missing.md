---
title: "My System&gt;Admin Menu Is Missing"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by whoeva on 2007-04-26
Hello, I originally posted this in the help section but got no replies so I'm tryiing here as I am also a total beginner when it comes to Linux.

Hopefully someone can help me fix this problem without needing a reinstall. I have Fiesty and am a total Linux virgin. Seems I have just managed to completely remove the admin menu from my system. All I have there is preferences and the "abouts" and exit. The administration menu is totally gone.

I don't know if it has anything to do with it but I just ran sudo apt-get clean which didn't appear to do anything but now my admin menu is gone.

Please can anyone help me?
Has this happened to anyone else?
Should I just go ahead and reinstall Fiesty in order to fix it?

Any advice would be very welcome here. Thanx.

---

### Post by seetho on 2007-04-26
Go to System->Preferences->Main Menu

Your Administration item is probably unchecked.

---

### Post by whoeva on 2007-04-26
Thank you for your quick reply. I did look in that area previously but it is missing from there too. I only have the preferences section listed in that window so I cannot check/uncheck the admin menu!

---

### Post by sarracenia88 on 2007-04-26
In the main menu, go down to Sytem. Click on system. You should see two icons for preferences and administration. If you only see preferences, then go over to new menu on the right hand side of the window and click new menu. Add these lines
[I]
Name: Administration

Comment: Change systemwide settings (affects all users)[/I]

Then just click close. you should see the new menu. If there are no icons, just tell me and I will give you the commands for those icons. 

I hope that you realize that making mistakes like this are the best ways to learn how to use linux. It forces you to find out how the system works.

Good Luck!

---

### Post by whoeva on 2007-04-26
Thank you for another quick reply. I have tried adding the menu as you suggest. It has not worked. The admin menu is not showing up in either the system menu nor the main menu editor thingy. I shouldn't need to restart X or reboot or anything for it to show up should I?

I am under the complete realisation that mistakes help the learning process. This is why I'm trying out this OS for the first time ever as I intend to avoid installation of any windoze versions on my new PC when I finally get around to building it sometime this year.

I'm very pleased with my Fiesty experience so far but am totally clueless as to why my admin menu has vanished or how to get it back and am trying to avoid another reinstall (messed up X before trying to get TV-out working!)

---

### Post by seetho on 2007-04-26
In the Main Menu editor, did you try to click on the button "Revert".  It is suppose to set your main menu back to the default installation.

Otherwise if you want to avoid a reinstallation then you can try adding the Administration menu and all the items under it manually.

st

p.s. I've reinstalled my system so many times I lose count.  That is part of the learning process.  Despite some problems I still find Linux far better to use than Windows.

---

### Post by sarracenia88 on 2007-04-26
Did you reinstall the menu like I told you to by clicking add new menu? You should get the admin window back, but you might not have all of the apps listed under that menu. If you don't see the apps, just post again saying so and I will give you the links for all of the app shortcuts. 

Also, kind of off topic, but you may want to also try out beagle. it works like finder in mac or the bottom of the start menu in vista. you can search all of your files and emails on your computer and I use the app all of the time.

About reinstalling, I remember that I had to do that about 3 times before I figured out how to do what I wanted to fix through the OS itself. It is different from windows so it takes a little getting used to, but it is well worth it. You can then brag to all of your friends that you have a fast, virus free computer that does everything you want it to do. I also suggest ordering about 3 pressed cds from shipit so you can give them to your friends once you have learned a little more about how to use the OS. that way you can help convert them too! :)

If you need more help just post.

---

### Post by whoeva on 2007-04-26
Yes I tried using the revert button and it did not bring back the admin menu and yes I have also tried several times to add the admin menu manually and it doesn't seem to be working.

Where oh where has my admin menu gone and why oh why cannot I not make it return?

---

### Post by sarracenia88 on 2007-04-26
If you wanted, one of us could do a remote desktop and try to help you figure out your problem. Do you know how to set this up from gnome? Just be careful who you let remote desktop to you because then they will have access to the computer. If you do find that the person is doing anything suspicious, you can unplug your ethernet cord so that they don't have access to your computer any longer. If you are interested in this route please post and we will help you further.

---

### Post by seetho on 2007-04-26
Try reinstalling ubuntu-desktop.

...or you can try what sarracenia88 suggested and let someone remote in to your system.  It may not be such a good idea if you have sensitive data on your systems.  On the other hand if you have no data of value in there then just do a reinstall.

I'm about to do mine.  I'm going backwards (I'm thinking 6.06)!  I installed Feisty and notice that my notebook now cannot recover from suspend and hibernate.  It also has trouble umounting usb drives.  All this was working before.  Oh well!  I half expected there will be problems by using a new release so soon.

Cheers.

---

### Post by whoeva on 2007-04-27
Ok, thanx again for the help. I tried using the sudo aptitude remove ubuntu-desktop command followed by sudo aptitude install ubuntu-desktop in the terminal but everything appears to be the same. ie. still no admin menu.

I'm grateful for the offer of help via a remote desktop but as I'm totally new to this operating system I am reluctant to go ahead with this. It looks like a complete system reinstall is the only way I can fix this but I'd really like to know how it happened or how I can fix without a reinstall else it may happen again!

I have a seperate partition for my home directory but if I do a reinstall of root I guess I will have to add all the programs I currently have added and reset all the settings etc or is there a way I can save my settings ie ktorrent, firefox, evolution etc?

---

### Post by sarracenia88 on 2007-04-27
Im not sure what else you can do. Reinstalling is one way to go, it could be that the first time you installed it, some file got corrupted. just backup your bookmarks and things on a flash disk or a cd and reinstall. 

To get to some of those files, there is a trick. It took me a while to figure out what it is but it is worth knowing. In your home directory, click view, then check show hidden flies. here are all of your config files. You can also press crtl h and that will do the same thing. I personally think that there is a corruption in one of your system files and a clean reinstall will help. Like I have said before, i had to reinstall several times before i had everything figured out. 

Don't be afraid to read the forums during some down time and learn what other users are doing. that's how I learned most of what I know about linux.

Good Luck!

---

### Post by whoeva on 2007-04-27
Oh, I do plenty of searching and reading but I couldn't find anyone else posting about a missing admin menu so that's why I made this post.

My PC is running XP as well as ubuntu so I can just copy required files over if I need to back anything up. I looked at the hidden files in my home folder and see all my progs and settings.

My question is if I do a reinstall of ubuntu on the root partition will these programs on the seperate home partition still operat or will I need to add them all again? From the look of it it would seem that if I leave the home partition alone and just reinstall ubuntu on the root then I should be able to just carry on as normal?

Is this the case or is it more complicated than I'm thinking?

BTW, the first/second time I installed everything was fine and my admin menu was ok but as stated in the first post here all of a sudden it vanished and I don't know why other than running that clean command.

---

### Post by seetho on 2007-04-28
> **whoeva said:**
> 
My PC is running XP as well as ubuntu so I can just copy required files over if I need to back anything up. I looked at the hidden files in my home folder and see all my progs and settings.

My question is if I do a reinstall of ubuntu on the root partition will these programs on the seperate home partition still operat or will I need to add them all again? From the look of it it would seem that if I leave the home partition alone and just reinstall ubuntu on the root then I should be able to just carry on as normal?


I suggest you backup your data to an external drive.  There was another thread here where someone trashed all of his HDs on his PC including the XP partitions when his Feisty upgrade went wrong.

For the install, when you partition the HD choose the manual method.  You will see the option to keep the existing data on your /home partition.

FYI I just replaced my Feisty with Dapper.  Everything (important to me) works now.  I'm happy.  I think I'll wait for the next LTS before changing.

Good luck.

---

### Post by sarracenia88 on 2007-04-28
i have feisty running just fine and I am very happy with it and its new features. I haven't run into too many problems with running it.

---

### Post by nosyguy on 2007-04-30
Hi,

I am also facing similar problem. I tried to re-arrange the shortcuts on the main menu, but now my "add/remove programs" shortcut is missing. When I create a new user, that user has it. So could someone  tell me the link to get it back on the main menu?

Thanks,
tay

---

### Post by nosyguy on 2007-04-30
Just found the answer I wanted:

In case anyone else have the same problem in future, and reached this page... below is the link:

[http://ubuntuforums.org/showthread.php?t=196557&highlight=add%252Fremove+missing](http://ubuntuforums.org/showthread.php?t=196557&highlight=add%252Fremove+missing)

---

### Post by AnThOnYhO on 2007-05-07
Hi you can open a terminal and su to root,
run  users-admin and click your name and go to the user privilege grant all privilege to your login name.
It be ok try it.
Sorry for my pool english.

---

