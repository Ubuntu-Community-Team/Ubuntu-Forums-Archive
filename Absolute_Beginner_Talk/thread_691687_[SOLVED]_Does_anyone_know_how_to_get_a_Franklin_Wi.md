---
title: "[SOLVED] Does anyone know how to get a Franklin Wireless CDU-680 USB modem working in"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jwill1515 on 2008-02-08
I got it working in Feisty no problem using the sudo ./connect command in the terminal program. I contacted Franklin and the gentleman told me to,

1. copy to desktop all files except 'itfchg'
2. open terminal and type "sudo ./itfchg/dev sd?
"?" being where the CDU-680 is located. in my case it was sdb, it may be sda or sdb
3. in terminal run execute.sh and modem will activate

I followed the above direction with no luck. I tried sda, sdb and sdc.
How do I tell what the sd? letter is and where the modem is located? I plug it in the front right USB slot on my HP Pavilion dv9205us. The printer is plugged in the rear right USB port directly in front of the power cord and I have a chill mat plugged in one of the left USB ports. There are four ports all together. I am new to Linux and this is all pretty confusing to me. I read some of the posts and I was getting more confused. I can't be that hard to get this modem working in 7.10. It worked no problem in 7.04. I must be doing something wrong. I would appreciate any help or advice.

---

### Post by Jewfro_Macabbi on 2008-02-08
Can the system be configured via system - network? Or using wvdial - edit /etc/wvdial.conf then execute sudo wvdial to connect.

Or is the problem it cannot detect the modem?

---

### Post by jwill1515 on 2008-02-09
Thank you for the reply. That's very kind of you. How do you configure via system-network? Do you type the command in terminal? A tried a wvdial command in terminal with no luck. I found the info from a Sprint website through a forum link. I used a Live CD of 7.04 and the modem connected with no problem. When I insert the modem it will show up as a folder on my desktop. Why would it work just fine on 7.04 and not 7.10? I had 7.10 installed on my computer at a Linux User Group meeting and they could not get the modem working either.

---

### Post by zekica on 2008-02-09
> **jwill1515 said:**
> 1. copy to desktop all files except 'itfchg'
2. open terminal and type "sudo ./itfchg/dev sd?
"?" being where the CDU-680 is located. in my case it was sdb, it may be sda or sdb
3. in terminal run execute.sh and modem will activate

I think you have to type:

[B]cd /path/to/folder/where/itfchg/is
sudo ./itfchg /dev/sd?[/B]

---

### Post by jwill1515 on 2008-02-09
Thank you for the reply. That's very kind of you. The itfchg file is in the USB device. How do I get there? cd what?

---

### Post by zekica on 2008-02-09
**cd /media/sd?1** maybe, You can see which folders are in /media by typing **ls /media**

---

### Post by jwill1515 on 2008-02-09
Thank you. Do you do this in terminal? So I type in ls/media when I'm in terminal? And then I type cd/media/sda1 or sdb1? What about the sudo ./itfchg/dev sda-b?

---

### Post by zekica on 2008-02-09
Yes, you do that in Terminal, but you have to type this exactly as I wrote (spaces where needed). You have written for example: **cd/media/sda1** you have to write this as **cd /media/sda1** (there is a space between **cd** and **/**.

---

### Post by jwill1515 on 2008-02-09
Thank you for the reply. I typed ls /media and it came back with

cdrom
cdrom0
CDU_680
sda1
sda2

When the modem is inserted in the USB port a folder is put on the desktop with all the files from the CDU-680 USB modem. When I try to get to the itfchg I typed in

cd /Desktop/CDU-680/ itfchg/dev/sda1

and tried all sorts of variations. It's not recognizing the CDU-680 folder sitting on the desktop as far as I can tell but I think I'm getting close. I really appreciate the help. Do you have a similar modem?

---

### Post by zekica on 2008-02-10
Ok, can you try to type *exactly* this:
[B]cd /media/sda1
sudo ./itfcfg /dev/sda[/B]

---

### Post by jwill1515 on 2008-02-10
Thank you, Zekica. I will give it a try. I'm pretty sure I tried that already.

---

### Post by jwill1515 on 2008-02-10
It recognized the cd /media/sda1command but came back with "command not found" with the sudo ./itfchg/dev/sda command. Is there a space betwwen the g and the /? Isn't the itfchg file located in the CDU-680 folder?

---

### Post by rkd on 2008-02-10
I found the Franklin web site and here are their Linux install directions:

```
1. Insert the CDU-680 USB Modem+DiskTM into an USB slot 
   on your PC. The device will be shown as a removable
   storage on your computer.
2. The script files are located under the &#8220;Linux&#8221; 
   directory. Copy the whole directory to your desktop.
3. Do the following steps:
   a. Open terminal
   b. Cd to Desktop/Linux
   c. Run "sudo ./connect"
   d. Enter root password
4. Device will switch to modem mode and attempt to connect.
5. To disconnect, press Ctrl-C twice.
```
These directions were for using the modem with Sprint. The directions for Qwest seemed the same. These directions seem different than what you wrote as the directions you got from calling Franklin. I don't know why the document on their web site gives different directions. I'd tend to believe the document than what the guy told you on the phone, but the document could be wrong.

In your post showing the output from ls /media, I see CDU-680 appears in the list, so I think it was recognized. So that seems to show Step 1 worked.

A simple way to do Step 2 is something like this: 
i. Click the Places menu at the top of the Ubuntu screen. Then click Home Folder, the first selection under Places.
ii. In the window that opens, double-click the Desktop icon, to open the Desktop folder.
iii. Go back to the Places menu and look for CDU-680. If you see it, click on it.
iv. Drag the window that opens until the previous window is also visible.
v. Find the Linux folder in the second window and drag it into the previous window. That should copy the Linux folder to your Desktop.

If you could not find CDU-680 in step iii, click on Computer in the Places menu instead. I think you will see CDU-680 in the window that opens. Double-click the CDU-680 icon, then pick up with step iv.

Now you should be able to do what it says in Step 3. The commands you enter should be:
```
cd   Desktop/Linux
sudo   ./connect
```
Remember that the commands have to be entered exactly as shown -- capital letters are different than small letters and spacing is significant. You can use the mouse to copy the commands from this post and paste them into the Terminal window if you want to be sure you enter them exactly.

After the sudo command, it prompts you for your login password. When you type the password in the Terminal, you will not see anything appear on the screen. That is normal -- it doesn't echo what you type so nobody can learn your password by looking over your shoulder. Just type your password carefully and push the Enter key after the last character of your password.

I don't know anything more about this. I've never used one of those modems. But if you try this advice and it doesn't work, post again, explain what went wrong, and I, or someone, will try to help.

In case you want to look at the Franklin web site, here is where I was looking: [http://www.fklt.com/support.php](http://www.fklt.com/support.php)

---

### Post by jwill1515 on 2008-02-10
Thanks for the reply. That's very kind of you. The current release of the CDU-680 software supports up to Linux Unbuntu 7.04. The instructions on the website work with 7.04. I have 7.10 installed on my computer and haven't been able to get the modem working. It worked with the 7.04 Live CD with the directions provided on the website. The PM and VP of Product Development at Franklin, Mr. Peter Won, wrote me "anyone who has used Linux for more than one day will be able to do this (the instructions he provided) without effort. Hope this helps until I find a fix for 7.10, which you hope me to send you as well." I will give your suggestions a try. Thank you very much for the info.

---

### Post by spiderbatdad on 2008-02-10
there may be a problem with the way wvdial.conf is written in Gutsy: semicolons or some other character at the beginning of the lines for phone number, username, password. edit the file with a text editor and remove the offending characters from those entries.

This is the main difference between wvdial.conf in 7.04 and 7.10. I struggled with this for two days before finding the solution.

---

### Post by jwill1515 on 2008-02-10
Thank you very much. Where is the file that needs to be edited?

---

### Post by spiderbatdad on 2008-02-10
```
gksu gedit /etc/wvdial.conf
``` after edit, click the floppy disk icon near the top of the window to save.

---

### Post by jwill1515 on 2008-02-10
Thank you. Is that a space in front of gksu gedit /etc/wvdial.conf? I type that in terminal and edit the characters in the file? I'm new to Linux.

---

### Post by spiderbatdad on 2008-02-10
yes...you can navigate to the file to look at it by clicking on. Places>>Computer>>File System>>etc... then scroll down to the bottom of the window and click on wvdial.conf. If it wont open, right click on it and select open with text editor. But you cannot edit the file this way. You must use the previous command gksu<space>gedit<space>/etc/wvdial.conf

---

### Post by spiderbatdad on 2008-02-10
once you find the file maybe select Edit from the window menu and select all...then Edit again and Copy...then come back and paste the file into a post...

---

### Post by jwill1515 on 2008-02-10
Thank you very much. I'll give that a try.

---

### Post by jwill1515 on 2008-02-11
The file looked ok. It contained,

[Dialer defaults]
Phone =
Username =
Password =
New PPPD = yes

Now what? The gentleman at Franklin said to 

1. copy to desktop all files except itfchg
2. open terminal and type sudo ./itfchg/dev sd? ("?" being where the CDU-680 is located)
3. in terminal run execute.sh

My question is how do I get to the itfchg file? When I type in ls /media I get

cdrom
cdrom0
CDU-680_umsd
sda1
sda2

---

### Post by spiderbatdad on 2008-02-11
I thought you were well past that stage. i would try```
sudo wvdialconf
``` in a terminal...no dot between wv and dial. Then cd into the Desktop/Linux file and```
sudo ./connect
```

I am convinced that dial-up connection is a vicious undertaking in Linux for anyone other than a software engineer.

---

### Post by spiderbatdad on 2008-02-11
you may need to run the scanModem tool prior to running wvdialconf  I dont know if you have a way to add it to your desktop and upack it by right clicking and selecting extract here...then cd into Desktop/scanModem and ./scanModem...then run wvdialconf again. I know this sux. sorry it is so hard...and I'm not even sure I'm helping.

---

### Post by jwill1515 on 2008-02-11
What do these things stand for when I type ls /media?

cdrom
cdrom0
CDU-680_USMD
sda1
sda2

Maybe if I understood a little more I could figure this out.

What will sudo wvdialconf do?

---

### Post by spiderbatdad on 2008-02-11
those commands only list what is in those locations. sudo wvdialconf writes the /etc/wvdial.conf file for you. Yours was basically empty.

---

### Post by jwill1515 on 2008-02-11
Thanks, you've been great. I've had people at a Linux User Group meeting look at it and they couldn't figure it out either in the limited amount of time they had. Where is Scanmodem tool? I think I did something like that and it couldn't find anything. Is it as cold in Vermont as it is here in Michigan? About -20 with the wind chill.

---

### Post by jwill1515 on 2008-02-11
I thought it was empty. Looked like I needed to add info.

---

### Post by spiderbatdad on 2008-02-11
all the files you have been looking for should be located in the zip file you downloaded from Franklin...if you only have a package, you should right click on it and select "extract here"

I just downloaded the zip file myself to read it. I also noticed that linux drivers were only available for the sprint and quest models.

Any way the folder you need to be in when you run ./connect is Linux_Ubuntu...you will probably need to open the CDU680_UMSD folder and drag the Linux_Ubuntu folder onto your desktop. then```
cd Desktop/Linux_Ubuntu
sudo ./connect
```

You can also read all the connect documentation in that folder.

We have our share of cold...a lot of snow this year...just keeps coming and coming.

---

### Post by jwill1515 on 2008-02-11
Those instructions are for 7.04. The modem works and connects just fine in 7.04 with those instructions but will not work in 7.10. I am using Sprint but I don't think that really matters. the modem is supposed to work with different services depending on your location. The files are actually in the USB device. I copied all the files except itfchg into a folder on the descktop I renamed Linux_Unbuntu.

---

### Post by spiderbatdad on 2008-02-11
the itfchg file is in the CDU folder, if you need to run it follow the same instructions for running ./connect:only ./itfchg

---

### Post by spiderbatdad on 2008-02-11
i notice an execute.sh file in there...read it...it may give you clues to how they renamed wvdial.conf...if you can track that configuration file down in /etc then you can check for the offending semicolons we talked about earlier...it seems to remove wvdial.conf and replace with wvdial.conf_log  or wvdialconf_sprintconfig

---

### Post by jwill1515 on 2008-02-11
How do I get to the itfchg file? When I type cd /Desktop/CDU-680_UMSD it comes back with no such file or directory. I know I must be doing something wrong.

---

### Post by spiderbatdad on 2008-02-11
I dont think that s the complete file path...it should be a folder located on your desktop called.CDU680_USMD_contents. in that folder is the Linux_Ubuntu folder containing all the other files, but according to instructions you should get those files from the device itself by mounting it on your desktop...ie. find it in Places>>Computer and click on it to mount it. If you've already been through all that, I still think you should look for the configuration file I mentioned before...maybe in /etc/wvdialconf_sprintconfig.
At any rate I see the itfchg file in Linux_Ubuntu

---

### Post by spiderbatdad on 2008-02-11
here's what one person went through:[http://beyondlimit.org/linux/How-To_CDU-680.html](http://beyondlimit.org/linux/How-To_CDU-680.html)

---

### Post by jwill1515 on 2008-02-11
Wow! I might have to go back to 7.04! The execute.sh file contents;

echo "--> CDU680DORA Linux Connection\n"
rm -rf sprintconfig wvdialconf_log
wvdialconf sprintconfig > wvdialconf_log
echo "Carrier Check= no\nStupid Mode= yes" >> sprintconfig
echo "Phone = #777\nUsername = sprintpcs\nPassword = sprintpcs" >> sprintconfig
rm -rf wvdialconf_log
echo "--> Dialing...\n"
wvdial --config sprintconfig

---

### Post by spiderbatdad on 2008-02-11
that looks like something! I was thinking the feisty thing all along, but didn't want to say it...just remember Hardy LTS is coming soon...Anyway does ```
lsusb
```at least show the device? and if it does you may need to modprobe it. take a look at the link:[http://beyondlimit.org/linux/How-To_CDU-680.html](http://beyondlimit.org/linux/How-To_CDU-680.html)

or you may try connecting now in the normal way...that last output looks like it wrote the file at least.

---

### Post by spiderbatdad on 2008-02-11
> **jwill1515 said:**
> Wow! I might have to go back to 7.04! The execute.sh file contents;

echo "--> CDU680DORA Linux Connection\n"
rm -rf sprintconfig wvdialconf_log
wvdialconf sprintconfig > wvdialconf_log
echo "Carrier Check= no\nStupid Mode= yes" >> sprintconfig
echo "Phone = #777\nUsername = sprintpcs\nPassword = sprintpcs" >> sprintconfig
rm -rf wvdialconf_log
echo "--> Dialing...\n"
wvdial --config sprintconfig

Thats just a script to dial out.

---

### Post by rkd on 2008-02-11
In searching the web, I have found several places where people report that they were able to get the Franklin CDU-680 working on Gutsy. Unfortunately, they didn't give enough details to tell me what you need to do.  Still, we know it is possible.

Did the gentleman from Franklin give you some steps to do before the ones you listed in the post that started this thread?

The reason I ask that is that the command```
sudo ./itfchg/dev sd?
```which I think really should be more like```
sudo ./itfchg /dev/sd?
```means it should run the program named itfchg from the current directory (the . means current directory). Since he said to copy all the files except itfchg to the desktop, he wouldn't expect you to find itfchg on the desktop, so he may have expected you to be in some other directory where the itfchg program actually is. Or could the command he told you to run actually have been the following?```
sudo /dev/sd?/itfchg
```That would make some sense to me -- although why you need to copy the other files to the desktop escapes me, unless you use them some time later, like to connect or something.

It should be pretty easy to find out where the CDU-680 is in the filesystem. Just enter the command```
mount
```It will list a lot of lines, most of which you can ignore. Just look for a line that has CDU-680, or something similar, in it. The name at the beginning of that line should be something like /dev/sdb -- whatever it is, that is the device name for your modem. Just for example, suppose it is /dev/sdb. Then I think the command the guy from Franklin wanted you to run would be```
sudo /dev/sdb/itfchg
```After that, you need to run the execute script. I imagine you do that by switching to the place where you copied the files, then entering the command```
./execute.sh
```I'm assuming execute.sh is among the files you copied to your desktop in the first step he gave you. If that is not true, then I don't know where execute.sh would be.

So, did you copy some files to the desktop? When you look at your computer screen, do you see them anywhere? If you don't see them, we can run a command to find them:```
sudo find  /  -name execute.sh
```If that finds something, copy the output and paste it into a post here and we'll see whether that gives us enough of a clue how to proceed. If that command doesn't find anything, try```
sudo find  /  -name connect
```If that finds something, post the output here.

Other's have gotten the device to work on Gutsy, so we should be able to do that, too.

Back in post #25, you asked what the output from ls /media meant.  /media is a directory within which Ubuntu automatically mounts external devices. The names that appear from ls /media are the names that you can use to look at the contents of the external devices. For example, if you had a disc in your CD drive, the command```
ls /media/cdrom
``` would show you the contents of the main directory of the disc.

You'll notice that one of the entries has a name, CDU-680_USMD, that seems to be related to your CDU-680. That indicates to me that Ubuntu has found your device.  I think that if you entered the command```
ls /media/CDU-680_USMD
```you would see the contents of the main directory of the storage part of your CDU-680.

The CDU-680 acts the same as a USB thumb drive when you first connect it to the computer. That itfchg program is supposed to turn on the modem part of the device (which apparently is not turned on automatically when you plug it in).

You seem not to be very familiar with the Linux command line commands. There probably is an easier way to look at the contents of the thumb drive part of the CDU-680. If you go into the Places menu on the Ubuntu desktop (up at the top of the screen), you might find that CDU-680 name listed. If it is there and you click on it, a file browser window should open and you can see what is on the device. If you don't see it in the Places menu, click on the Computer entry in the Places list, and you'll probably see it in the file browser window that opens then.

Let me mention that I know almost nothing about these wireless modems. I'm a fairly broadly-experienced computer jockey, so I can make guesses about things like this that often turn out to be helpful, but sometimes my guesses are wrong.

---

### Post by jwill1515 on 2008-02-11
Thank you very much. Those were the only instructions the gentleman at Franklin gave to me. The execute.sh file is on the desktop with the other files except itfchg. The itfchg file is in the USB device. I will try your suggestions and post back.

---

### Post by rkd on 2008-02-11
I found a post that clarifies what the itfchg command should look like. My first guess was right, not my second guess.

That is, the command should be something like this:
```
sudo  ./itfchg  /dev/sd?
```You determine what the ? should be as I described in my earlier post.

That still leave the question about where the itfchg program is and what directory you should be in when running that command.  It seems to me that the directions from the guy at Franklin that you should copy everything except the itfchg program must be wrong. I think you should copy all of the files, use a cd command to change into the directory that contains the itfchg file, then run the command above.

I'll post more if I come across better information.

---

### Post by rkd on 2008-02-11
Ah, our posts crossed.

Given that you see the files on the desktop, when you open the terminal, you would get into that directory using the command```
cd Desktop
```
But if the itfchg program hasn't been copied there, you won't be able to run it. I think you should copy the itfcfg file to the desktop, too. Then after cd Desktop, the sudo command will find the program.  You still have to determine the proper /dev/sd? name, but I showed you how to do that.

Once you have run the itfchg command, then the ./execute.sh command should work, since the execute.sh file is in the desktop, which still will be your current directory.

---

### Post by jwill1515 on 2008-02-11
Thank you. mount command said the CDU680 was ar sdb. I tried all the commands you suggested with no luck but I have not copied the itfchg file yet. I will copy it and try again.

---

### Post by jwill1515 on 2008-02-11
I copied the itfchg file to the desktop and typed cd Desktop/Linux_Unbuntu and got to the directory.  When I try to run the sudo ./itfchg command it comes back with "file not found". I tried all sorts of variations
sudo ./itfchg/dev/sdb
sudo ./itfchg /dev/sdb
sudo .itfchg/dev sdb
sudo /dev/sdb/itfchg
etc

---

### Post by rkd on 2008-02-11
When you said the files were on the desktop, did you really mean that the files were in the directory Linux_Unbuntu, which, in turn was on the desktop? Maybe the terminology is confusing to you.  And is that directory named Linux_Unbuntu or Linux_Ubuntu? Like in grade school, spelling counts!

Let's do this -- open a new Terminal enter the following commands, and paste the output into a post here.```
pwd
ls -l
cd Desktop
ls -l
cd Linux_Ubuntu
ls -l
```If you are reading the forums on your Ubuntu system, you can run those commands by using the mouse to highlight and copy the text right from the browser window, then move to the Terminal window, paste, put the Enter key to run the last command. If that directory really is named Linux_Unbuntu, my cd command for Linux_Ubuntu will get an errror. If that happens, just type the cd command with the correct name then do the ls -l command after that.

Now you have all the commands and the output from them in the Terminal.  Now use the mouse to highlight everything from the pwd command to the end of the output of the last command, click Copy from the Edit menu of the Terminal window, come back to the browser, start a new post in this thread, paste the text you copied into the new post, and submit it. That will let me and anyone else looking see just what you are seeing.

If you aren't reading the forum on your Ubuntu system, then you could open an editor, paste the output you copied from the Terminal window into he editor's window, save the text into a file, then move that file to your system you use for the forums in whatever way is convenient -- on a USB Flash drive, on a floppy disk, or whatever.  If you need to do this, but aren't sure how, post asking for more help -- and give me an idea of how you might best move the text file and I'll try to give you more instructions.

---

### Post by yellowbread on 2008-02-11
I don't know if I'll have enough time to finish this before I have to go to work, but here's how you get that modem connected.

The simple way is to use the connect program that Franklin ships with the modem. 

1. Copy the entire directory Linux_Ubuntu from the modem to some place, the Desktop will work fine.
2. Open a terminal and cd into the Linux_Ubuntu directory with

cd ~/Desktop/Linux_Ubuntu

3. Run the command 

sudo ./connect

This does several things: changes the device to modem mode (itfchg), writes a configuration file for wvdial, then invokes wvdial. To disconnect, hit ctrl C twice.

This method has a few annoyances besides the fact that it sometimes hangs, saying some device (/dev/sdb, /dev/sdc, etc) needs read/write permissions. It rather ungraciously unmounts the device, and it leaves you with an open terminal while you are connected.

Gotta go get ready for work now, I'll check back later and try to give alternatives to the above.

---

### Post by jwill1515 on 2008-02-11
Thank you. I will work on it later. I am at work now. I might have made a mispelling somewhere. I'll have to check that out. Yes, the files are in the folder I created. I am reading forums in Explorer/Vista as I cannot get modem to work in Ubuntu 7.10. It works in 7.04 Live CD. I can print the instructions and type them in Ubuntu. Thanks for your time. I really appreciate it. I will post back later when I can work on it again.

---

### Post by jwill1515 on 2008-02-11
Thanks yellowbread, I really appreciate the time and effort, but those instructions work and are for 7.04. The instructions will not work in 7.10. The gentleman at Franklin said the device was supported up to 7.04 and gave me directions for 7.10 (see top of thread). Any other suggestions? Why would the modem work in 7.04 and not 7.10?

---

### Post by spiderbatdad on 2008-02-11
The reason would be the way wvdial.conf gets written...those semicolons, but you have yet to get all the files from the device and run them.

---

### Post by jwill1515 on 2008-02-11
Thank you spiderbatdad. I'm sorry, I'm stupid. I don't understand what you're trying to tell me.  "...those semicolons, but have yet to get all the files from the device and run them." I copied all the files to the desktop into a folder I named Linux_Ubuntu, the same name that the folder is called in the USB device. Could that be the problem? I tried running the commands that I have been instructed to do in all sorts of variations. I know I must be doing something wrong. When I open terminal it says something like jwill1515@jwill1515laptop. From there I cd Desktop\Linux_Ubuntu trying to get to the itfchg file. I'm right there but can't run the sudo comands.

---

### Post by spiderbatdad on 2008-02-11
check to see if you have anything in /etc/wvdial.conf now, and if so post it here. Do you have the ltfchg yet, if not I can try to send it to you...or you can get it at the Franklin site.

---

### Post by rkd on 2008-02-11
spiderbatdad: 

Could you be a little more clear about what you believe the problem is with wvdial.conf? From what you wrote, you had the problem and solved it simply by removing some improper characters from that file.  But I don't see the connection between that and what the guy from Franklin told jwill1515 about how to make the modem work. Can you see the connection?

Do you happen to know how wvdial.conf is supposed to get written? That might shed light on why it gets written incorrectly.

Did you have to do anything else besides removing some characters from the wvdial.conf file in order to make things start working on Gutsy?

jwill1515:

Try not to worry much about why the commands didn't work for you. When you have a chance to run the commands I gave you to show what files are in the various places, I'm sure we will quickly home in on why the command isn't working for you. I'm just concerned that there is more to the puzzle than getting that command to execute.

It would be interesting to compare the wvdial.conf file now with what it was in Feisty. Are you still able to boot your computer with Feisty? When you upgraded to Gutsy did you save any of the files from Feisty? How did you upgrade -- did you do a fresh install of Gutsy, completely wiping out Feisty, or did you do a dist-upgrade to install Gutsy over Feisty? If the latter, it might have saved a copy of wvdial.conf before updating it.

---

### Post by spiderbatdad on 2008-02-11
I'm not sure his program has written to wvdial.conf yet. His command sudo ./connect from the directory Desktop/Linux_Ubuntu  seems to return command not found, and the execute.sh script, as I have looked at it, seems to remove wvdial.conf and replace it with another config file. I know that in Feisty, the wvdialconf command wrote to the file with semicolons in front of phone#, username, and password....gnome-ppp wrote the file that way as well. It had to be patched in Gutsy to remove the semicolons.

this post: [http://beyondlimit.org/linux/How-To_CDU-680.html](http://beyondlimit.org/linux/How-To_CDU-680.html) ,though for suse, might correct a modprobe error, as well as offer some other help. I still have not seen his device mounted with a lsusb output.

I suspect he should mount the device, scanModem it, get a proper wvdial.conf...for usb modem, then try to run sudo ./connect from the Linux_Ubuntu directory. It's a shame Franklin went through the trouble to provide drivers and connection software to Ubuntu, and a distro-upgrade renders the stuff useless. That isn't good.

---

### Post by jwill1515 on 2008-02-11
Thank you very much, rkd. I appreciate your time and effort. I am new to Linux. I freshly installed 7.10 at a Linux User Group meeting last week. I am going there again tomorrow evening. I have a dual boot configuration now. I can choose to run Ubuntu or Vista. I have a 7.04 disk that the people at the user group gave me. We couldn't get that to work at the time. You have to type noapic irqpoll noirqdebug to get Ubuntu to work on my HP Pavilion dv9205us, cone to find out. After the install of 7.10, I tried running the 7.04 Live CD after reading some comments on the forum and the modem connected and worked just fine following the instructions provided by Franklin (sudo ./connect). Should I un-install 7.10 and install 7.04? That would be an easy solution for me. How would I go about doing that?

---

### Post by jwill1515 on 2008-02-11
Following is the e-mail sent by Franklin:

John,

Our current release supports up to Linux Ubuntu 7.04.

Please follow a simple way to solve any tech support problems with the interface changer in Linux Ubuntu 7.10

1; copy to desktop all files except 'itfchg'

2; open 'terminal and type "sudo ./itfchg /dev sd?" 

"?" being where the CDU-680 is located. In my case it was "sdb", it may be &#8220;sda&#8221; or &#8220;sdb&#8221;

3; in terminal run "execute.sh" and the modem will activate and connect to the internet.

 anyone one who has used Linux for more than a day will be able to do this without effort. hope this helps until I find a fix 7.10 which you hope me send to you as well.
 
Please let me know your results.

 Thanks

 Peter Won

PM and VP of Product Developments

 Franklin Wireless Corp.

9823 Pacific Heights Blvd. Suite #J

San Diego, CA 92121

TEL: 858-623-0000 (Ext. 108)

FAX: 858-623-0050

Mobile: 858-775-0837

[http://www.franklin-wireless.com](http://www.franklin-wireless.com)

 From: John Williams [mailto:jwilliams@reflexind.com] 
Sent: Wednesday, February 06, 2008 8:37 AM
To: [email]cs@franklin-wireless.com[/email]
Subject: Can't get CDU-680 to work with Linux_Ubuntu 7.10

I'm a Millenicom customer. They asked me to contact you. I followed the instructions provided and even had some other people from a Linux User group look at it with no luck. Any suggestions? I'm using a HP Pavilion dv9205us, 2gb RAM, dual AMD Turion processors. Thanks.

 John Williams

---

### Post by spiderbatdad on 2008-02-11
Jwill1515 could you post the result of ```
lsusb
```with the device plugged in?

---

### Post by jwill1515 on 2008-02-11
I'll have to do that for you later. I'm at work right now and the computer is at home. I'll try it again this evening and post back. Thank you for all your help.

---

### Post by spiderbatdad on 2008-02-11
I think fixing modprobe with the output from lsusb may be the solution.

---

### Post by rkd on 2008-02-11
John:

Here I was thinking that you somehow garbled the instructions that Franklin gave you (I thought you had to copy them down in a phone call). But now I see that Franklin *sent* you already garbled instructions. I don't know anything about Franklin, and I have to give them some credit for offering support for Linux users of their equipment. But I have to say that whoever wrote those instructions was a bit sloppy -- maybe in a hurry or something. There simply is no way they will work as given -- I can see at least three obvious mistakes. It does make me wonder how careful they were about writing the Linux setup code that has stopped working with Gutsy -- it might not be Gutsy's fault. On the other hand, a lot of other things have stopped working in Gutsy, so the Gutsy release was not as well-checked-out as it ought to have been. So it could be either Ubuntu's fault, or Franklin's fault, or a little of both that the setup doesn't work on Gutsy.

So, should you switch to Feisty? Hard to say. You were able to get the Live CD of Feisty to run and to get the modem to work properly on Feisty.  That's points for Feisty. But the Linux User's Group guys couldn't get Feisty installed on your computer. That's at least a yellow flag -- maybe you would have other trouble with Feisty, although it might be that the problems the Linux User's Group guys were having were all due to not specifying the "noapic irqpoll noirqdebug" options. Like I said, it is hard to say whether to switch to Feisty. I have a feeling that once we get past the setup, the modem will work okay on Gutsy, so I'd say it might be less work to press on trying to get it to work on Gutsy. We do know that other people have managed to get it to work, spiderbatdad for one, and I saw posts from several others, too. But if you would rather switch to Feisty right now, that's fine. We could lead you through it on the forum, but if you can get the folks at the Linux User's Group to help you with it, that probably would be easier for you -- helping someone in person is alway quicker and easier for both parties than trying to work through a forum like this. Now that you know those options that have to be specified to get Feisty to run on your computer, the Linux Users Group guys should have no trouble getting Feisty installed.

So think about those possibilities and decide which way you'd like to go. I'll help you down any of the paths as best I can.

---

### Post by jwill1515 on 2008-02-11
Thanks rkd. I'd really like to stick with Gutsy if at all possible. Yes, the guys at the user's group didn't know the whole noapic irqpoll noirqdebug option. I found that in a forum somewhere. So which of the commands are garbled and what are the right commands? I'll try again this evening and I'll let the gentlemen at the user's group take a look at everything tomorrow evening. Thanks to everyone.

---

### Post by rkd on 2008-02-11
Okay, we'll continue to try to get it working on Gutsy.

Here are the commands Mr. Won gave you, with my notes about what is wrong beneath the commands I'm talking about. I get the impression that you are as yet unfamiliar with Linux commands, file navigation, etc., so some of the terms I use here might not be clear to you. At the moment, I don't think you need to understand all these details (though I agree, it would be nice for you to understand what is going on). But I believe you'll become more familiar with this stuff as you gain experience.

> 1; copy to desktop all files except 'itfchg'
Nothing obviously wrong with the above, except it seems odd not to copy itfchg, since the next command wants to run it.

> 2; open 'terminal and type "sudo ./itfchg /dev sd?"

"?" being where the CDU-680 is located. In my case it was "sdb", it may be “sda” or “sdb”
Two obvious problems with the above. First, when you open a terminal, your current directory is your home directory. The sudo ./itfchg says to run the itfchg command which is in the current directory ("." is current directory). Since step 1 didn't tell you to put the itfchg file into your home directory (it told you not to copy it anywhere), this command will certainly fail.

The second problem with the above command is that the "/dev sd?" part of the command really should be "/dev/sd?", at least according to one of the other threads on the topic I found, the parameter after itfchg is supposed to be the path to the modem.

> 3; in terminal run "execute.sh" and the modem will activate and connect to the internet.
This command wants to run the execute.sh file, but just as before, it isn't in the current directory (it is on the desktop, or maybe in a folder on the desktop, not in your home directory). 

After I see the output from the commands I asked you to run in post #45, I'll be able to tell you precisely what commands I think you should run.

By the way, did you understand what I said in that post about copying the output from the commands from the Terminal window into a text file and moving that text file to the system you use to access the forums? If not, try to get that clear before trying those commands in post #45 so you can easily post the results (it might not be very practical to try to reproduce them by hand).

---

### Post by jwill1515 on 2008-02-11
Thank you rkd. I'm having to switch between Vista and Ubuntu right now because of the modem not working in 7.10. I've already determined that the USB device is on sdb. How come when I type in "ls /media" I get,

cdrom
cdrom0
CDU680_UMSD
sda1
sda2

Where is sdb and why is it not showing up when I type ls /media? Or is CDU680_UMSD sdb? What is sda1 and sda2. I printed from Ubuntu last evening with no problem. Is the printer listed under "ls /media". Would the printer be sda1 or sda2? sda1 appears on the desktop and looks like it's all the files under Vista. Sorry, I'm just trying to understand. I'll try your suggestions when I get home in about two hours. Thanks.

---

### Post by rkd on 2008-02-11
Be careful -- USB devices don't always come up as the same device name. Check it each time you need to know the device name.

/media is where removable storage devices are placed when they are connected to the computer.

I'm pretty sure that /media/CDU-680_UMSD is /dev/sdb, or whatever your modem happens to be called this time. I think you said in one of your posts that when you looked at the output of the mount command, it showed you that /dev/sdb was connected to /media/CDU-680_UMSD.

I can't immediately tell you what /media/sda1 and /media/sda2 are. One of the might be your Windows partition. Maybe both are Windows partitions if the computer had more than one partition before you installed Ubuntu. I haven't hooked up a printer to my Ubuntu test system yet, so I don't know how a printer shows up yet.

There are a number of commands that can tell you various things about what is mounted under /media. You would enter these in a Terminal window.```
mount
sudo fdisk -l
```The mount command's output isn't formatted very readably, but it tells what device is mounted where in your system. The fdisk command's output is a nice tabular display and shows information about each disk and the partitions on them. I imagine you will be able to spot a few things in the output of both of those commands, but probably won't understand them completely.  If you copy the output of those commands and put it into a post, I'll explain it in some detail so you can understand it better. (When you paste output into a post, after you've pasted it, go back and highlight it, then click on the # icon that is third from the end of the icons above the message composition window. That will make sure the text gets displayed faithfully in the post.)

About the printer: As I said, I haven't hooked one up to my Ubuntu test system yet, but I just did a quick web search for information and found that an old-style parallel port printer usually is named /dev/lp0 while a newer USB port printer is usually named /dev/usb/lp0. I imagine that if you open an editor (such as gedit - Applications -> Accessories -> Text Editor) or a word processor (such as Open Office - Applications -> Office -> OpenOffice.org Word Processor), then go to the File menu and select Print, it will show you the names of the printer or printers it knows about.

All of your devices are somewhere under /dev. You don't always use those names directly, but ultimately, any reference to a device ends up going through a /dev entry.

I don't know what your chill mat is. It might be one of those devices that just takes power from the USB port and doesn't have any other role. I don't know whether such things would appear somewhere under /dev or not. I suspect they would not, but I don't know for sure.

---

### Post by spiderbatdad on 2008-02-11
```
lsusb
```

Have you abandoned the idea of trying to modprobe, as I've suggested all along? rkd seems to have decided to take over. If you want to get back to what we were working on...according to the fix I have pointed you to, feel free to PM me.

---

### Post by jwill1515 on 2008-02-11
Thanks for the reply spiderbatdad. I'm printing your instructions right now and will try shortly. I just got in from work and just started looking into it again. Thanks for your help.

---

### Post by yellowbread on 2008-02-11
Since the short solution doesn't work for you here's the long solution.

I have a CDU-680 working in both Gutsy and Hardy (alpha 4). To get it to work there are two things you have to do. First, you have to get the modem into modem mode as opposed to data mode. Second, you have to configure a dialer to connect using the modem.

For the first step, you can use the itfchg program supplied by Franklin. The program opens the modem device /dev/sda, /dev/sdb or whatever your modem happens to be, then does a FIBMAP ioctl call on the open device, with data telling it to change to mode1 (modem mode). If for any reason it is unable to open the file, it gives the (usually incorrect) message that it needs read/write permissions for the device. The program itself does not try to figure out which device is the modem, so you have to tell it which device to use. To find out which device is your modem, in a terminal issue the command 

```
cat /proc/scsi/sg/device_strs
```

This displays in the terminal the contents of a file that contains a list of all the scsi devices connected to your computer. When I do it, here's what I get.

```

filbert@filbert-desktop:~$ cat /proc/scsi/sg/device_strs
ATA             ST3320820AS             3.AH
ATA             ST3320620AS             3.AA
Generic         USB SD Reader           1.00
Generic         USB CF Reader           1.01
Generic         USB SM Reader           1.02
Generic         USB MS Reader           1.03
CMOTECH         Mass Storage            2.31

```

The first device in the list is /dev/sda, the second is /dev/sdb and so on. My results show the modem (CMOTECH) at /dev/sdg.

Before you change the mode on the modem, it is best if you unmount it. Here's how.
```

sudo umount /media/CDU680_UMSD
```

I assume you have itfchg somewhere on your computer. Change to its directory and run the infamous itfchg command. For me this would be
```

sudo ./itfchg /dev/sdg

```

At this point the modem should be in modem mode. Linux then does some stuff in the background. In particular, the cdc_acm driver recognizes the modem and assigns it to /dev/ttyACM0.

You can check if this has happened with the command

```
ls /dev/ttyACM*
```

Here's what happens when I do this.

```
filbert@filbert-desktop:~$ ls /dev/ttyACM*
/dev/ttyACM0
```

If for some reason you get more than one device listed here, your modem is most likely on the last one in the list.

If the itfchg program fails to do the trick, let me know. I wrote a program which changes the mode that you can have.

Now for the second step, configuring the dialer. I'm going to show you how to configure wvdial.

First run 

```
sudo wvdialconf
```

The output should look like this:

```
filbert@filbert-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

Now go in and edit /etc/wvdial.conf
```

gksudo gedit /etc/wvdial.conf
```

Make sure the semicolons are removed from the front of the lines (those comment out the line),
set the lines Phone, Username,  and Password as below. If you want include the Stupid Mode line too. The modem will connect more quickly if its included

```
Phone = #777
Username = anything
Password = anything
Stupid Mode = on
```

The username and password are not checked by sprint, so it really doesn't matter what you use.

Save and exit the file.

Now to connect all you have to do is invoke wvdial. In a terminal:
```

wvdial
```

To disconnect, enter ctrl c twice.

---

### Post by jwill1515 on 2008-02-11
These are the results I got;

jwill1515@jwill1515-laptop:~$ lsusb 
Bus 002 Device 003: ID 03f0:5811 Hewlett-Packard  
Bus 002 Device 002: ID 0c45:62c0 Microdia  
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 002: ID 16d8:6803   
Bus 001 Device 001: ID 0000:0000   
jwill1515@jwill1515-laptop:~$ pwd 
/home/jwill1515 
jwill1515@jwill1515-laptop:~$ ls -l 
total 108 
drwxr-xr-x 3 jwill1515 jwill1515  4096 2008-02-08 20:09 Desktop 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Documents 
lrwxrwxrwx 1 jwill1515 jwill1515    26 2008-02-05 15:46 Examples -> /usr/share/example-content 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Music 
-rw-r--r-- 1 jwill1515 jwill1515 77824 2008-02-11 01:17 nautilus-debug-log.txt 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Pictures 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Public 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Templates 
drwxr-xr-x 2 jwill1515 jwill1515  4096 2008-02-05 20:51 Videos 
jwill1515@jwill1515-laptop:~$ cd Desktop/ 
jwill1515@jwill1515-laptop:~/Desktop$ ls -l 
total 4 
drwxr-xr-x 2 jwill1515 jwill1515 4096 2008-02-11 07:41 Linux_Ubuntu 
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/ls -l 
bash: cd: Linux_Ubuntu/ls: No such file or directory 
jwill1515@jwill1515-laptop:~/Desktop$

---

### Post by yellowbread on 2008-02-11
Careful with your typing. You hit / instead of enter after the last cd.

---

### Post by jwill1515 on 2008-02-11
Thanks yellowbread,

jwill1515@jwill1515-laptop:~$ cat /proc/scsi/sg/device_strs 
ATA             TOSHIBA MK1234GS        AH00 
HP              Photosmart C5180        1.00 
CMOTECH         Mass Storage            2.31 
jwill1515@jwill1515-laptop:~$ sudo umount /media/CDU680_UMSD 
[sudo] password for jwill1515: 
jwill1515@jwill1515-laptop:~$ cd Desktop/ 
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/ 
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo ./itfchg /dev/sdc 
sudo: unable to execute ./itfchg: No such file or directory 
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ 

So the modem is sdc, right?
The itfchg file is in the Linux_Ubuntu folder I copied to my desktop.
Why can't I get there??? I must be doing something wrong. I just noticed I missed a space after itfchg.

---

### Post by spiderbatdad on 2008-02-11
```
cd Desktop/Linux_Ubuntu
sudo ./itfchg /dev/sdc
```

---

### Post by jwill1515 on 2008-02-11
No luck,

jwill1515@jwill1515-laptop:~$ sudo umount /media/CDU680_UMSD 
jwill1515@jwill1515-laptop:~$ cd Desktop/ 
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/ 
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo ./itfchg /dev/sdc 
sudo: unable to execute ./itfchg: No such file or directory 
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$

---

### Post by spiderbatdad on 2008-02-11
do you have the iftchg in Linux_Ubuntu, if you click on the folder?

---

### Post by rkd on 2008-02-11
I think you are having trouble because you are trying to follow three different people's directions.

Back at the beginning, you said that you followed the Franklin guy's directions to copy all the files except itfchg to the desktop.

Now you are trying to run itfchg from the desktop (actual from Linux_Ubuntu which is on the desktop).

Naturally, it can't find itfchg if you didn't put it there.  I'm assuming you didn't copy it there without mentioning that you did so.

We would have found out for sure had you not made a typo when carrying out my instructions to show what files are on your desktop.

I'll step back and just watch. Maybe you'll get farther if you are only trying to follow two people's directions.  If you need me, ask.

---

### Post by jwill1515 on 2008-02-11
All the files, including the itfchg file, are in the folder I copied to the desktop. I opened the folder to confirm. How do I get to the itfchg file on the USB device? Do I need to? There is also a folder called CDU680_UMSD on the desktop which contains all the files in the USB device.

---

### Post by jwill1515 on 2008-02-11
All the info is helpful. I appreciate everyone's help.

---

### Post by rkd on 2008-02-11
Perhaps the itfchg file is not marked as executable.

Show us the output of ls -l when you are in the Linux_Ubuntu directory.

---

### Post by jwill1515 on 2008-02-11
rkd,

I pasted the results of what you wanted me to do. I guess I typed something wrong in the last command. That's probably what you needed to see, right?

---

### Post by rkd on 2008-02-11
Yes, you made a typo and so the results did not show the contents of the Linux_Ubuntu directory.  I think I know what we'll see, but I want to be sure before telling you what to do. You've been trying so many things, I think we need to verify each step. Open a Terminal and enter these commands:
```
cd Desktop/Linux_Ubuntu
ls -l
```
Copy the output and put it into a post here.

---

### Post by yellowbread on 2008-02-11
Now that you mention it, I remember on a fresh install of gutsy that the same thing happened to me. Trying to run itfchg or connect from a directory where I knew they were present, both gave me the error you got. I went on with my business setting up Gutsy the way I wanted it, and after some installs and updates (mostly stuff to compile gnome-ppp so I could apply a patch, build-essential etc.) and a few reboots, it started working.I don't know what changed to make it work.

What I'm suggesting now is pure guesswork. You could try copying itfchg to somewhere in your path (sudo cp ~/Desktop/Linux_Ubuntu/itfchg /usr/local/bin/) and then try the sudo itfchg /dev/sdc again. Note that when it is in your path, you don't need the ./ in front of itfchg. So here are the commands:copy the file with

```
sudo cp ~/Desktop/Linux_Ubuntu/itfchg /usr/local/bin/
```

If you want check to make sure it got there

```
ls /usr/local/bin/i*
```

Invoke itfchg

```
sudo itfchg /dev/sdc
```


 And yes it appears that your modem is /dev/sdc

---

### Post by jwill1515 on 2008-02-11
Here you go;

jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ ls -l
total 36
-rwx------ 1 jwill1515 jwill1515 9452 2007-11-20 11:45 connect
-rwx------ 1 jwill1515 jwill1515  332 2008-02-11 01:16 execute.sh
-rw------- 1 jwill1515 jwill1515  332 2007-11-20 11:45 execute.sh~
-rwx------ 1 jwill1515 jwill1515 7724 2007-11-20 11:45 itfchg
-rwx------ 1 jwill1515 jwill1515  244 2007-11-20 11:45 Linux connect steps.txt
-rw-r--r-- 1 jwill1515 jwill1515   90 2008-02-09 13:19 sprintconfig
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$

---

### Post by rkd on 2008-02-11
That probably won't do any good -- after the copy, the file won't be executable. You didn't tell him to do a chmod. Don't have him put an extraneous file into his /usr/local/bin.

---

### Post by yellowbread on 2008-02-11
> **rkd said:**
> Perhaps the itfchg file is not marked as executable.

Show us the output of ls -l when you are in the Linux_Ubuntu directory.

Good suggestion.

---

### Post by yellowbread on 2008-02-11
> **rkd said:**
> That probably won't do any good -- after the copy, the file won't be executable. You didn't tell him to do a chmod. Don't have him put an extraneous file into his /usr/local/bin.

He can always take it back out again.

---

### Post by jwill1515 on 2008-02-11
All I did was the ls -l command. I'm having to switch between Vista and Ubuntu.

---

### Post by rkd on 2008-02-11
Oops, my apologies -- the copy with sudo will preserve the executable bit.

But the itfchg is marked executable by owner. I don't know why it won't run. Maybe copying it to /usr/local/bin is worth trying.

---

### Post by spiderbatdad on 2008-02-11
```
 modprobe usbserial vendor=0x16d8 product=0x6803
```

according to what research i have done, there is a modprobe error with the device, i dont know why itfchg is not running.

---

### Post by jwill1515 on 2008-02-11
Thank you very much spiderbatdad. Everyone's been great. I've gotten a lot of help and have learned a little along the way. Do I need to run the above modprobe command?

---

### Post by spiderbatdad on 2008-02-11
yes i believe you do...then follow yellowbreads instructions from the top

---

### Post by jwill1515 on 2008-02-11
Is that a space before the modprobe command?

---

### Post by spiderbatdad on 2008-02-11
no space before the command

---

### Post by yellowbread on 2008-02-11
> **spiderbatdad said:**
> yes i believe you do...then follow yellowbreads instructions from the top
 I tried that once when I was trying to figure out what itfchg did. Without the modem in modem mode, nothing worked. The modem gives device ID 6843 when its in modem mode, 6803 when its in data mode. So I doubt it will work, but it won't hurt either, and who knows?

---

### Post by jwill1515 on 2008-02-11
jwill1515@jwill1515-laptop:~$ modprobe usbserial vendor=0x16d8 product=0x6803
FATAL: Error inserting usbserial (/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-11
mmm sorry  sudo modprobe you can use the up arrow key to scroll through previous terminal commands...then left/right arrow to move around and put sudo at the front of a command so you don't have to retype everything.

---

### Post by spiderbatdad on 2008-02-11
how about:```
cd Desktop/Linux_Ubuntu
sudo chmod a+x itfchg
sudo ./itfchg /dev/sdc
```

---

### Post by spiderbatdad on 2008-02-11
> **yellowbread said:**
> I tried that once when I was trying to figure out what itfchg did. Without the modem in modem mode, nothing worked. The modem gives device ID 6843 when its in modem mode, 6803 when its in data mode. So I doubt it will work, but it won't hurt either, and who knows?

if he runs ```
sudo wvdialconf
```he should get some useful output, such as the location of the modem ie, USB0

then presumably create a symbolic link```
sudo ln -s /dev/ttyUSB0 /dev/sdc
```

---

### Post by jwill1515 on 2008-02-11
jwill1515@jwill1515-laptop:~$ sudo modprobe usbserial vendor=0x16d8 product=0x6803
jwill1515@jwill1515-laptop:~$ cat /proc/scsi/sg/device_strs
ATA             TOSHIBA MK1234GS        AH00
HP              Photosmart C5180        1.00
CMOTECH         Mass Storage            2.31
jwill1515@jwill1515-laptop:~$ sudo umount /media/CDU680_UMSD
umount: /media/CDU680_UMSD: not found
jwill1515@jwill1515-laptop:~$ cd Desktop/Linux_Ubuntu/sudo ./itfchg /dev/sdc
bash: cd: Desktop/Linux_Ubuntu/sudo: No such file or directory
jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo ./itfchg /dev/sdc
sudo: unable to execute ./itfchg: No such file or directory
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$

So I should try sudo wvdialconf? Or sudo chmod a+x itfchg
sudo ./itfchg /dev/sdc?

---

### Post by spiderbatdad on 2008-02-11
definitely run ```
sudo wvdialconf
``` and post the output from the terminal

---

### Post by jwill1515 on 2008-02-11
That's all? How bout modprobe or any of the others?

---

### Post by spiderbatdad on 2008-02-11
yes thats all...should have tried this long ago

---

### Post by jwill1515 on 2008-02-11
jwill1515@jwill1515-laptop:~$ sudo wvdialconf
[sudo] password for jwill1515:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-11
ok. that's not so good.  You might try```
sudo modprobe usbserial vendor=0x16d8 product=0x6803
``` then again with 6843 as the last four digits. It can't hurt anything.

then try```
sudo wvdialconf
```again.  Ideally itfchg would do wvdialconf for you, but we haven't been able to run it.
 Perhaps you need to run it from within the modem directory on your desktop. dont you show a directory CDU680_USMD...try cd into that directory to run ./itfchg /dev/sdc

---

### Post by jwill1515 on 2008-02-11
No luck. The only thing I haven't tried yet is sudo chmod a+x itfchg command you mentioned earlier. What do you all think?

---

### Post by jwill1515 on 2008-02-11
When Ubuntu first loads (with the modem in) it puts a folder on the desktop named CDU680_UMSD. I can click on the folder to open it and look at the contents. It seems that I can't access it from terminal by typing cd Desktop/CDU680_UMSD. yellowbread says to unmount the drive in one of his first instructions.When I do that the folder disappears.

---

### Post by spiderbatdad on 2008-02-12
editted: you are doing great. proceed to next post...chmod a+x will solve your problem

---

### Post by spiderbatdad on 2008-02-12
definitely have to run the following to make itfchg and connect executable```
cd Desktop/Linux_Ubuntu
chmod a+x itfchg
chmod a+x connect
``` Then you will be able to run ./itfchg

when you are running sudo ./itfchg, you are doing so as other...I changed permissions as above and it ran fine. This is a basic step for all executables. We should have had you do this 50 posts ago. If you run```
ls -l
```again while you are in the Desktop/Linux_Ubuntu directory, you will see itfchg and connect have turned green, where before they were white, and you will see the permissions have changed to -rwx-rx--x

---

### Post by jwill1515 on 2008-02-12
Thank you. I will give that a try and post back later this evening. I'm supposed to go to a Linux User Group meeting this evening, if I can make it there, and I will have someone from there try to help me through this also.

---

### Post by rkd on 2008-02-12
jwill1515:

In post #103 you wrote something that reveals a bit of a misunderstanding.

I doubt this has any bearing on getting the modem to work, except to the extent that it might muddle communication between you and the others, but I figured you would like to understand a little better how things work.

(This explanation is for the normal Ubuntu, using the Gnome desktop interface, not for Kubuntu or any of the other desktop interfaces. I know nothing about how those other desktop interfaces work yet.)

You said that when Ubuntu loads with the modem plugged in, it puts a folder on the desktop, but it doesn't let you access it when you enter a cd Desktop/CDU-680_USMD command. That reveals a misunderstanding.

From what I've read in some other places, your CDU-680 consists of two devices in one unit: One of the devices is the data modem, the other device is a USB storage device (much like those little USB Flash drives or USB Thumb drives that are like solid-state disks).

When you plug in the CDU-680 (or start Ubuntu with the device plugged in), Ubuntu mounts the USB storage device portion of the unit on /media/CDU-680_USMD (or maybe on /media/CDU680_USMD -- you are inconsistent in how you spell it in your posts). It might appear as an icon on your screen (in fact, I would expect it to appear as an icon on your screen, but you haven't described that, as far as I remember), but I haven't seen any evidence that plugging in the device puts anything into the Desktop directory. 

If you entered a command```
ls -l /media/CDU-680_USMD
```(or the other spelling, if this isn't the correct spelling), that should show you the top level contents of the USB storage portion of your CDU-680 device. The command```
ls -l Desktop/CDU-680_USMD
```will give an error because Ubuntu doesn't put anything in your Desktop directory when the device is plugged in.

On my test system, when I login, there are two icons on my screen. They represent two partitions on my hard disk. They appear in /media, NOT in /home/rkd/Desktop. My /home/rkd/Desktop directory is empty. If I create a file named x in /home/rkd/Desktop, a third icon, labeled x, appears on my screen, right beside the other two icons. There are some entries in the /media directory on my computer that don't show up on the main screen -- for instance, an entry for my CD-ROM drive and an entry for my floppy drive. When I put a disk in either device, an icon for that device then appears on the main screen alongside the other icons.

So it is very easy to get confused -- Ubuntu mixes together the things in /media and in your Desktop directory and displays them together on the main screen of your computer. If there is an easy way to distinguish visually which of those icons represent something in /media vs. which of them represent something in your Desktop directory, I don't know what it is. I guess it is just something that you get a feeling for, with experience.

If I right click one of the icons on my screen and select Properties from the menu, the ones that came from /media show a Location: as "on the desktop". The one that actually is in my Desktop directory shows Location: as "/home/rkd/Desktop".

So the term "Desktop" or "on the desktop" is kind of confusing. I've seen the large area on the screen between the top bar and bottom bar referred to as "the desktop", even in "The Official Ubuntu Book". But not everything that appears in that area comes from your Desktop directory -- the devices that get put into /media when they are mounted also appear there.

Usually when someone says "on the desktop, they mean "in your Desktop directory" but the Properties display for an icon on the desktop uses the term "on the desktop" to mean something that came from /media. I don't know the history of this, and there might be more details about it than I have discovered, so I might not have laid out the entire story here.

The take away ideas for you to absorb are:

1. The term "on the desktop" seems to be a bit ambiguous. Be careful when you see it or use it to take into account that it is ambiguous.

2. The items represented by icons that appear on the main screen are a mixture of things from /media which represent devices that currently are accessible and things from your Desktop directory.

You can use the File Browser (Applications -> Accessories -> File Browser) to look at the contents of various directories instead of using ls commands. To start at the root directory (/), double-click the icon "File System" in  the left part of the File Browser display. To start in your home directory, double-click on the icon for your userid in the left part of the File Browser display. 

I used the ls commands in my examples because they are much more compact than explaining how to navigate to a place in the File Browser. I think it would help you understand things a little bit better if you learned how the things you see in the File Browser correspond to the path names in ls commands (and, really, in any command line command). I don't know how you can best learn that because it has been so long ago that I absorbed that stuff that it is very hard for me to remember how someone who doesn't understand it views things. I've searched the web for a good introductory explanation of that, but I haven't found one.

Your CDU-680 also contains a data modem device, but that apparently is not automatically activated when you plug in the device. The itfchg program that you are having so much trouble getting to run is supposed to turn on the data modem portion of the device. When the data modem gets turned on, Ubuntu does NOT make an entry for it in /media -- it makes an entry for it with a name like /dev/ttyACM0, or something similar. The software that uses the modem to establish your connection to the internet will use the /dev/ttyACM0 device to communicate to the internet. I don't know whether it will also use the /media/CDU-680_USMD device or not -- I kind of doubt it, but I don't know. (I read about this on some other site, and one of the other guys here has also said some stuff about it -- I don't know whether you picked up on it though, so I thought I'd mention it again here to be complete.)

---

### Post by jwill1515 on 2008-02-12
Thanks for all the info, rkd. It's very helpful and that's very kind of you. Yes, when Ubuntu loads there is a folder(maybe it's an icon. I'm at work right now and don't have access to computer Ubuntu is on) called CDU680_UMSD (no -) that appears to be on the desktop. When I click on it to open it doesn't give a path or anything so I just assumed it was on the desktop. So I have the device plugged in. I'm suppossed to unmount it and then run the sudo ./itfchg command from the folder I copied to the desktop? Or do I cd /media/CDU680-UMSD and run the sudo itfchg command from there without unmounting? If I unmount then the CDU680_UMSD folder that is "on the desktop" disappears. Can I still access it by cd /media/CDU680_UMSD?

---

### Post by yellowbread on 2008-02-12
rkd, I was just about to say something along those lines. I'm glad you got there first. You said it much better than I could have.

jwill1515, from my experience, no attempts to get the modem recognized by a driver work until the modem is put into modem mode. Focus on getting itfchg to run.

1. Because it appears there is some confusion on this part, make sure the Linux_Ubuntu folder is copied somewhere. As rkd pointed out, the CDU680_USMD icon you get on your desktop is not located in /home/jwill1515/Desktop. But you can simply drag the Linux_Ubuntu folder from there to the desktop. A command line option to do the same would be

```
cp -rf /media/CDU680_UMSD/CDU680-UMSD-contents/Linux_Ubuntu/ ~/Desktop/
```

2. Now cd to the Linux_Ubuntu folder on your desktop

```
cd ~/Desktop/Linux_Ubuntu
```

3. Unmount. The reason for this is that iitfchg unsafely unmounts the device.

```
sudo umount /media/CDU680_UMSD
```

4. Run itfchg

```
sudo ./itfchg /dev/sdc
```

---

### Post by spiderbatdad on 2008-02-12
Dont forget to chmod a+x itfchg  and connect, and probably execute.sh...anything in that folder you plan on running. This is the reason you have not been able to run ./itfchg successfully, nor will ./connect run.  I am not 100% sure why the user group set to rwx is not enough, except to guess that running as sudo, is part of the "other." Permissions can be tricky to understand. The 3 groups are user, group, and other...in that order, often denoted ugo, and the permissions are read, write, execute, denoted, rwx. At the beginning, you may see a dash, or a "d" or an "l." This is related to what type of file or directory is being listed. 

Unfortunately, sudo chmod commands cannot be used in the form of chmod -rwxr-xr-x, to set the permissions, which would be the equivalent of: user=read, write, execute...group=read, execute...other=read execute.
Instead chmod is used in two ways that I know of. One is where a numerical value is assigned to each permission. read=4, write=2, execute=1. So ```
sudo chmod 755 itfchg
``` would give that file (or program) permissions of User=read, write, execute. Group=read, execute, Other=read, execute.  If you are the owner of the file, for example, files you create in your home directory, you do not need the sudo command before chmod (though it wont hurt anything), and indeed you will see that you don't need sudo to run chmod on itfchg, because user (that's you) is already rwx. You can write changes to the file.

The other way of changing permissions is to use the letters rwx and add or subtract them from ugo.  For example, chmod ugo+w itfchg  adds the write permission to all 3 categories, user, group, and other. The other, existing permissions would remain the same.  As I used chmod a+x itfchg, the "a" represents "all" which is the same as if I had typed: chmod ugo+x itfchg.

Anyway, there are numerous explanations of the Linux flie system permissions available on the web, and I may have done a poor job in explaining them, but hopefully, provided an adequate introduction.

---

### Post by rkd on 2008-02-12
jwill1515:

When you umount (NOT unmount -- watch the spelling carefully), that means you won't be able to access the device via the /media/CDU680_UMSD name -- it is no longer connected to the device after the umount.

I'm just going to watch the thread. Follow the directions from yellowbread and spiderbatdad -- they've actually used the device. I haven't. If they run out of ideas and I can think of something, I'll chime in, but it isn't good to have too many people giving directions at once on a forum like this -- it's too hard to coordinate to make sure that one person's directions don't interfere with another's.

yellowbread: 

Seems to me that the cp command you recommended might drop the executable flag on the copies of the files. Perhaps you should amend your directions to take that into account.

---

### Post by rkd on 2008-02-12
Perhaps it would be good to look at the permissions the files have on the CDU-680 device before copying them and make sure they have the exact same permissions on the copies.

---

### Post by yellowbread on 2008-02-12
The permissionsfor the files on the device are rwx for the owner, nothing for anyone else. The copied files have the same permissions. Thanks for the suggestion. I am fairly new to Linux so I don't always remember all important things. I did first try the commands I gave in my last post to make sure they worked as advertised, albeit on Hardy instead of Gutsy.

---

### Post by spiderbatdad on 2008-02-12
Owner is not actually a class of file permissions. The classes are "user," "group," and "other," in that order.  The file is said to be owned, but this is not a class of permissions. For example, a file could be owned by root, but have permissions -rwx------. Which would mean only the user, or logged in person, would have any permissions. Such a file could not be run system wide. It could not be run with sudo.

Now if the same file where to undergo chmod a+x  **file**, the new permissions would be:
-rwx--x--x. This file could be run system wide with the sudo ./command.

I tried to run ./itfchg several times, as we have outlined in this thread. It returned "bash: command not found," until I tried chmod a+x itfchg.   Then ls -l showed the new permissions, executable by all the classes,  itfchg appeared green in the terminal list, and it ran.

Regards.

---

### Post by jwill1515 on 2008-02-12
Thanks spiderbatdad. What exactly do I need to do. I just tried running the chmod commands and they appeared green but sudo itfchg wouldn't go.

---

### Post by spiderbatdad on 2008-02-12
Were you in cd Desktop/Linux_Ubuntu? And was itfchg in that directory? And was the device mounted? And did you do: ```
sudo ./itfchg
```. If all of the above are true, you must have had some new output.  Also you should chmod a+x everything in Linux_Ubuntu, and follow Yellowbread's instructions. Or you might try  sudo ./connect,  as the manufacturer suggests.

At any rate, If you're in the right directory, and all the files are executable with  chmod a+x, then they will run.

---

### Post by spiderbatdad on 2008-02-12
The permissions I have for the files in Linux_Ubuntu are -rwxr-xr-x. This is the same as 755. So the easiest thing to do, to make sure your files will run properly is```
cd Desktop/Linux_Ubuntu
sudo chmod 755 itfchg
sudo chmod 755 connect
sudo chmod 755 execute.sh
sudo ./connect
```

A faster way would be sudo chmod 755 *

That would change everything in the directory to -rwxr-xr-x

---

### Post by jwill1515 on 2008-02-12
Yes, I was in the Linux directory and the file is in there. I believe I umounted before I ran any commands. That is the first instructions on his list. Do I chmod execute.sh? What do I do first?

---

### Post by spiderbatdad on 2008-02-12
See my last post. Are you going to meeting tonight? Just curious.

---

### Post by jwill1515 on 2008-02-12
Yes, I'm there right now. They are making a presentation. I'll get back to you shortly. Thank you.

---

### Post by spiderbatdad on 2008-02-12
so your next step should be to umount the storage part of the device. ```
cd Desktop/Linux_Ubuntu
sudo ./itfchg
cd
``` is supposed to do that according to Yellowbread...or put the thing in data mode. Use dmesg to see if the usbserial module is loaded:

```
dmesg | grep usbserial
```
(nothing shows up)

The next command should be.```
sudo modprobe usbserial vendor=0x16d8 product=0x6803
```

Use dmesg to make sure it worked:

```
dmesg | grep usbserial
```
usbcore: registered new interface driver usbserial
usbcore: registered new interface driver usbserial_generic


then...```
sudo wvdialconf
``` Now you should get a fair amount of output. Please post that output, and we can make a symlink to the device.  You will also want to edit /etc/wvdial.conf to remove any semicolons at the beginning of lines...hopefully all goes as planned.

---

### Post by jwill1515 on 2008-02-12
Don't I have to cd to where itfchg is? And I do that first? Is it sudo modprobe?

---

### Post by jwill1515 on 2008-02-12
Looks like I umount first, then cd to itfchg, then (sudo?) modprobe?

---

### Post by jwill1515 on 2008-02-12
So I start with the chmod commands, umount the device, cd to itfchg, then (sudo?) modprobe?

---

### Post by spiderbatdad on 2008-02-12
well...before the modprobe, it is suggested to make sure the storage part of the device is unmounted with ```
dmesg | grep usbserial
```  You should see nothing...unless you have some other device plugged in. Then modprobe....Then dmesg again to see the module loaded....then sudo wvdialconf

No cd into itfchg...just ```
cd
``` after you run umount.

---

### Post by jwill1515 on 2008-02-12
So when I open terminal what's the first thing you want me to do? There's no sudo before modprobe this time?

---

### Post by spiderbatdad on 2008-02-12
there should be sudo before modprobe...sorry If I left it out....try to follow steps as posted in #121

---

### Post by jwill1515 on 2008-02-12
Don't I need to do the chmod 755 commands before I umount, then cd itfchg, etc.?

---

### Post by spiderbatdad on 2008-02-12
make sure everything in Linux_ubuntu is chmod 755. I have fixed post 121 to the best of my ability to make it more accurate, and easy to follow. I assume you have already changed the permissions in the folder...you don't have to do it everytime.   With your patience and perseverance, you are sure to be a Linux expert soon.

Unfortunately, if you manage to get it to write the /etc/wvdial.conf file, when you run sudo wvdial from the terminal, you may get a seg fault, if not the first time...then the next. It has something to do with the two modes of the device. Yellowbread posted he had a script to fix the problem. Another author ended up using kppp to run the modem.  Whatever, it has proven to be a great learning tool.

---

### Post by jwill1515 on 2008-02-13
Thank you spiderbatdad. So I chmod everything in the Linux_Ubuntu folder that I copied to my desktop and then umount and then start at the top of post 121. I will post back with results later this evening. The people at the Linux User Group meeting only provide minimal help last evening, They were busy with there own things and the two gentlemen that were helping me last week didn't show up this week. I want to mention that when we istalled Ubuntu 7.10 last week we just got through the install when it came time to leave. They said there was more to do but they didn't have time. For instance, there are drivers that need to be added or configured (nvidia, wireless, etc.). I could probably get them if only I could get this modem working in 7.10. I tried getting what I needed through the 7.04 Live CD but I guess it didn't take. I live in a rural area and the only access to any high speed service is Hughes.net satellite or Millenicom, which provides the CDU680.

---

### Post by spiderbatdad on 2008-02-13
Ideally you would get access to a high-speed ethernet connection temporarily to complete your 7.10 installation, and obtain a copy of the 7.10 live cd. You may be able to add some packages, like "build-essential" from your 7.04 cd. If you add that cd to your sources.list, aptitude will request the cd when you attempt to install a Ubuntu package contained on the cd.

Almost certainly, when you do get connected, all your Gusty sources will be commented out in your /etc/apt/sources.list. Please see my instructions for enabling sources on an installation where no internet connection was present at the time of the installation. 

[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

You will see, at the top of the list, is my 7.10 cd as a source. If you add the exact title of your cd there ( with no # mark), you should be able to use it to help you install some packages. I would recommend build-essential. I don't know If linux-restricted-modules is on the 7.04 cd. Of course Ubuntu will mail you a free copy of 7.10

```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
``` 

might work. I really haven't tried working without internet, and to use that command, you will of course, had to have enabled the sources...and or cd as discussed above. Good Luck.

---

### Post by jwill1515 on 2008-02-13
Thanks for the reply. I had hoped to get connected last night at the meeting but that didn't happen. I have access to dial-up. I downloaded 7.10 from the Ubuntu site and made a cd. I also have a disc coming in the mail. So, should I do all that first before trying to get the modem working?

---

### Post by spiderbatdad on 2008-02-13
I would look for Yellowbread's post in this thread later tonight: [http://ubuntuforums.org/showthread.php?t=682596](http://ubuntuforums.org/showthread.php?t=682596)

And, it certainly won't hurt for you to try to enable your sources or install build-essential off the live cd.

---

### Post by jwill1515 on 2008-02-13
Hre's some food for thought;

jwill1515@jwill1515-laptop:~$ gksu gedit /etc/apt/sources.list
jwill1515@jwill1515-laptop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                             
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US           
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                     
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                             
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
  Could not resolve 'archive.canonical.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
  Could not resolve 'archive.canonical.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-amd64/Packages.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jwill1515@jwill1515-laptop:~$

jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ ls -l
total 36
-rwxr-xr-x 1 jwill1515 jwill1515 9452 2007-11-20 11:45 connect
-rwxr-xr-x 1 jwill1515 jwill1515  332 2008-02-11 01:16 execute.sh
-rw------- 1 jwill1515 jwill1515  332 2007-11-20 11:45 execute.sh~
-rwxr-xr-x 1 jwill1515 jwill1515 7724 2007-11-20 11:45 itfchg
-rwx------ 1 jwill1515 jwill1515  244 2007-11-20 11:45 Linux connect steps.txt
-rwxr-xr-x 1 jwill1515 jwill1515   90 2008-02-09 13:19 sprintconfig
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo ./itfchg
sudo: unable to execute ./itfchg: No such file or directory
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo modprobe usbserial vendor=0x16d8 product=0x6803
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ dmesg | grep usbserial
[ 3035.931773] usbcore: registered new interface driver usbserial
[ 3035.932032] usbcore: registered new interface driver usbserial_generic
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$

---

### Post by yellowbread on 2008-02-13
The part that perplexes me is where the file itfchg is clearly there with execute permissions for everyone, but it still won't run.

Try this: In a terminal, cd to the Desktop, create a file called test, put the single line "echo it works" (without the quotes) in it, change its mode to executable by everyone, then run ./test. Here's how


```

filbert@filbert-desktop:~/Desktop$ cat > test
echo It works!
filbert@filbert-desktop:~/Desktop$ chmod a+x test
filbert@filbert-desktop:~/Desktop$ ./test

```

You will need to hit "enter" after the line cat > test and ctrl d after entering the line "echo It works!"
Of course you will type only the stuff after the $ prompt on each line. The result should be a line: It works!

I'm just curious if your gutsy has trouble running other things which should have no problems..

---

### Post by spiderbatdad on 2008-02-13
bill@bill-laptop:~/Desktop/Linux_Ubuntu$ ./itfchg
itfchg Usage:
        ra <device>
        device: /dev/sda /dev/sdb

bill@bill-laptop:~/Desktop/Linux_Ubuntu$ sudo ./itfchg
[sudo] password for bill:
itfchg Usage:
        ra <device>
        device: /dev/sda /dev/sdb


bill@bill-laptop:~/Desktop/Linux_Ubuntu$ ls -l
total 28
-rwxr-xr-x 1 bill bill 9452 2007-05-02 15:50 connect
-rwxr-xr-x 1 bill bill  332 2007-05-05 07:11 execute.sh
-rwxr-xr-x 1 bill bill 7724 2007-05-02 16:00 itfchg
-rwxr-xr-x 1 bill bill  244 2007-08-20 14:09 Linux connect steps.txt

---

### Post by jwill1515 on 2008-02-13
I got that test to work. It wouldn't go at first. For some reason I had to hit ctrl d twice to get it to work.

---

### Post by spiderbatdad on 2008-02-13
Have you tried running ./connect? Do you get the same Bash: connect command not found?

---

### Post by jwill1515 on 2008-02-13
Yes, I believe I do. I'll try it again. Any other suggestions anyone? I tried enable sources also before I messed with the modem. Did I do that correctly? I'm more concerned about the modem.

---

### Post by spiderbatdad on 2008-02-13
Well nothing got updated, but that's ok. You don't have a connection. I was thinking you would install build-essential using the cd, but that really isn't important right now...it's not like you're trying to compile ./itfchg, you just want to run it.

All I can think of right now is user privileges...clearly you can have administrative privileges. There are some other options under System>>Administration>>Users and Groups...You click your name then select properties on the right, then the user privileges tab. There are choices like...allow user to connect with modem, etc. This is probably not the issue. Something else is wrong since bash doesn't recognize itfchg as file. Like I said, I had the same result until I made it executable by all. So, I'm stumped for the time being.

---

### Post by yellowbread on 2008-02-13
Thanks for testing that for me. Yes, I have four other things to suggest. 

1. As I speculated some time ago, itfchg might work if you copy it to a location in your path.

```
sudo cp ~/Desktop/Linux_Ubuntu/itfchg /usr/local/bin
```

Then

```
sudo itfchg /dev/sdc
```

2. Try using the program I wrote that replaces itfchg. Spiderbatdad gave the link a few posts back.
Of course, without a working modem, installing build-essential might be a problem.

3. Try booting a Feisty Live CD, and running itfchg from there, then do a warm reboot. The modem's mode is preserved when you do a warm reboot.

4. Download the updates for gutsy via vista, and copy them to a USB stick or cd rom to install on Gutsy. I think then itfchg would run.

---

### Post by spiderbatdad on 2008-02-13
Yellowbread, I was thinking he could get build-essential off the live cd as a source. One post I was reading regarding this problem with bash states that he might not have the correct libraries to run the program. For example:" I suspect (but do not KNOW) that this is what happens when you try to run
a program that was compiled on a libc-based system on a glibc system (or
vice versa). The file permissions, etc all look OK (they ARE ok), but it 
doesn't run because the libraries are not the right ones at all."

---

### Post by jwill1515 on 2008-02-13
I looked at that link cdu-680/itfchg-source code. The program looks like it was wriiten by Franklin. It is under the first post by Paul86fxr. Where's your program? What do you mean by a warm reboot? Where do I get the updates for gutsy, from the Ubuntu site? That's where I got 7.10 from. When I have the disk in my cd/dvd drive it's name is Ubuntu 7.10 amd6. I have the AMD version because I have AMD processors. Does any of that matter?

---

### Post by spiderbatdad on 2008-02-13
I don't want to interrupt yellowbread, if he responds, but you should be able to ```
sudo apt-get install build-essential
``` if you have your live cd checked as a source in System>>Administration>>Software Sources...check the box in the dialog window that shows the CD. Then you should be asked to "reload"  After that apt-get should request the cd when you try to install build-essential. It has to be the cd you used for your install. An upgrade from an existing Feisty installation probably wont work.

---

### Post by yellowbread on 2008-02-13
Its down there in post #7. A warm reboot is where you restart the computer without shutting it off. As for where to get the updates, let's worry about that if it gets that far.

Spiderbatdad, that's very interesting. It means my suggestion of copying the file to a path location would not work, but that using my program would. That's kind of what I was thinking because of his test results with my little shell script.

By the way, thanks for setting me straight on the names of the permissions categories. I guess I ran into the old problem of how making up your own terminology works great until you actually try to communicate with somebody.

---

### Post by spiderbatdad on 2008-02-13
Yellowbread I think he'll still need build-essential for your program...and I make up my terminology as I go.:popcorn:  You were actually correct in saying owner (jwill1515)
had full permissions. I was unsure if sudo had any permissions. I don't really know all that much.


So here's the code. Copied from Yellowbread's post.
Code:

```
#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/fs.h>
#include <strings.h>

/* Returns the line number and the line itself for the line in inputfile that begins with inputstring
   Returns 0 if there is no such line
   Returns -1 and prints an error message if the inputfile can't be opened*/
int find_line(char *inputfile, char *outputline, char *inputstring, int inputlength){
        FILE *fp;
	int linenumber = 0;

	if((fp = fopen(inputfile,"r"))==NULL){
		printf("Unable to open %s.\n", inputfile);
		return -1;
	}
	do{
		if(fgets(outputline, 128, fp)==NULL) return 0;
		linenumber++;
	} while(strncmp(outputline,inputstring,inputlength));
	fclose(fp);

	return linenumber;
}

int main(int argc) {
	char file[26];
	char string[20];
	char devicename[9];
	char line[128];
	int fd;
	struct {
		unsigned int inputlength;
		unsigned int outputlength;
		char data[10];
	} ifchg;

	sprintf(devicename,"/dev/sda");
	sprintf(string,"RDEVCHG1");
	ifchg.inputlength = 9;
	ifchg.outputlength = 0;
	ifchg.data[0] = 0xff;
	memcpy(ifchg.data + 1,string,strlen(string));

	//Check if the device is plugged in and recognized, if so, get the /dev/sd? value.
	sprintf(file,"/proc/scsi/sg/device_strs");
	sprintf(string,"CMOTECH");
	devicename[7] += find_line(file,line,string,strlen(string)) - 1;
	if(devicename[7] < 'a'){
		printf("Modem not found.\n");
		return 1;
	}

	//Check if the device is mounted, if so, unmount it.
	sprintf(file,"/etc/mtab");
	sprintf(string,"/media/CDU680_UMSD");
	if(find_line(file,line,devicename,strlen(devicename)) > 0) umount2(string ,1);

	//Change the mode.
	if((fd = open(devicename,O_RDWR)) <= 0) {
		printf("Unable to open modem.\n");
		return 2;
	}
	usleep(800);
	ioctl(fd,FIBMAP,&ifchg);
	close(fd);
	
	return 0;
}
```

Copy and paste this into a file, save it as anything.c the name doesn't matter, give it a .c extension. cd to wherever you saved the file and then compile with
Code
```

gcc anything.c
```

You will need the package build-essential to do this. There will be a couple warnings that you can safely ignore when it compiles. The result is a file called a.out. You can rename a.out to anything you like, eg changemode with
Code:

```
mv a.out changemode

```
Then run
Code:

```
sudo ./changemode
```

to get the cdu680 into modem mode. The cdc_acm driver now claims the modem and assigns it to /dev/ttyACM0. You can run wvdialconf to confirm this. The rest is between you and your dialer.
__________________

---

### Post by yellowbread on 2008-02-13
You're right, build-essential will still be needed. Time for bed, I'll check back later.

---

### Post by spiderbatdad on 2008-02-13
BTW. anything.c compiled fine for me, and produced a.out.

---

### Post by jwill1515 on 2008-02-13
Getting close...

jwill1515@jwill1515-laptop:~$ sudo apt-get install build-essential
[sudo] password for jwill1515:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7416kB of archives.
After unpacking 31.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88046 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu9_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch/patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ gcc itfchg-source.c
itfchg-source.c: In function &#8216;main&#8217;:
itfchg-source.c:44: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
itfchg-source.c:44: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
itfchg-source.c:70:2: warning: no newline at end of file
jwill1515@jwill1515-laptop:~/Desktop$ mv a.out changemode
jwill1515@jwill1515-laptop:~/Desktop$ sudo ./changemode
jwill1515@jwill1515-laptop:~/Desktop$ cd
jwill1515@jwill1515-laptop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6279': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo ./connect
sudo: unable to execute ./connect: No such file or directory
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo itfchg ./dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ cd
jwill1515@jwill1515-laptop:~$ itfchg
bash: itfchg: command not found
jwill1515@jwill1515-laptop:~$ sudo itfchg
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-13
WOOT!   sudo wvdialconf    you left out sudo so you didnt have permission.

also to run those bin files you need ./ forexample sudo ./itfchg   though yellowbread's program replaces itfchg.

---

### Post by jwill1515 on 2008-02-13
I didn't do any wvdial commands. it did that itself.

---

### Post by jwill1515 on 2008-02-14
What next? Do I need to sudo wvdialconf? Bin files? sudo ./itfchg?

---

### Post by spiderbatdad on 2008-02-14
ok try this.  ```
sudo wvdialconf
``` I'm going to look to see why it did it by itself.

if wvdialconf works...check /etc/wvdial.conf to make sure it doesn't have those semicolons or just try to connect. You should be able to connect by running```
sudo wvdial
```

if sudo wvdial doesn't work, try sudo ./changemode again...assuming wvdialconf went smoothly in writting the file.

---

### Post by jwill1515 on 2008-02-14
I tried to edit the wvdialconf file but it wouldn't let me. It said I wasn't the owner and I didn't see where I could change permissions or anything.


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>


also...

jwill1515@jwill1515-laptop:~$ sudo wvdialconf
[sudo] password for jwill1515:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
jwill1515@jwill1515-laptop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
jwill1515@jwill1515-laptop:~$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jwill1515@jwill1515-laptop:~$ cd Desktop/
jwill1515@jwill1515-laptop:~/Desktop$ gcc itfchg-source.c
itfchg-source.c: In function &#8216;main&#8217;:
itfchg-source.c:44: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
itfchg-source.c:44: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
itfchg-source.c:70:2: warning: no newline at end of file
jwill1515@jwill1515-laptop:~/Desktop$ sudo ./changemode
jwill1515@jwill1515-laptop:~/Desktop$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
jwill1515@jwill1515-laptop:~/Desktop$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<Err>: Configuration does not specify a valid phone number.
WvDial<Err>: Configuration does not specify a valid login name.
WvDial<Err>: Configuration does not specify a valid password.
jwill1515@jwill1515-laptop:~/Desktop$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
jwill1515@jwill1515-laptop:~/Desktop$ sudo ./connect
sudo: ./connect: command not found
jwill1515@jwill1515-laptop:~/Desktop$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop$ connect
The program 'connect' is currently not installed.  You can install it by typing:
sudo apt-get install connect-proxy
bash: connect: command not found
jwill1515@jwill1515-laptop:~/Desktop$ sudo apt-get install connect-proxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package connect-proxy
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/execute.sh
bash: cd: Linux_Ubuntu/execute.sh: Not a directory
jwill1515@jwill1515-laptop:~/Desktop$ cd Linux_Ubuntu/
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ execute.sh
bash: execute.sh: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ connect
The program 'connect' is currently not installed.  You can install it by typing:
sudo apt-get install connect-proxy
bash: connect: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop/Linux_Ubuntu$ 
 
Thanks to everyone for the help. It's been outstanding.

---

### Post by spiderbatdad on 2008-02-14
Well, you've done great, and you're close. You should not need ./connect or ./itfchg any longer. I noticed you tried itfchg /sda /sdc a couple of times but left off ./

To edit /etc/wvdial.conf you want use gksu gedit. that will give you permission and a text editor to edit with.```
gksu gedit /etc/wvdial.conf
```  According to yellowbread, sprint doesn't require authentication, but fill in fake values for phone number, username and password.  Save /etc/wvdial.conf

When you want to connect you run: ```
sudo wvdial
```  now you will need to run ./changemode, i believe anytime you restart...I'm assuming your modem will mount in data mode...but I don't know for sure.

You may end up needing a different dialer other than wvdial. You could try ppp the graphical one that is displayed in the system network monitor in your panel.  kppp is supposed to be really good, but you'll need a way to copy it to you ubuntu system.

If you want to try to run the modem with ./connect, maybe you still need a few libraries. I would suggest checking synaptic to see that you have   libc6-i686, libstdc++6,

Start by fixing /etc/wvdial.conf

---

### Post by yellowbread on 2008-02-14
You are very close now. As spiderbatdad suggested, edit /etc/wvdial.conf with

```
gksu gedit /etc/wvdial.conf
```

Change the three lines with semicolons

```
Phone = #777
Username = anything
Password = anything
```

Ie, take the semicolons away from the beginning of the lines. The phone number to dial is #777, but the username and passwork can be anything you want. If you like, add the line

```
Stupid Mode = on
```



Then to connect:

```
wvdial
```

And remember, to quit do ctrl c twice.

---

### Post by jwill1515 on 2008-02-14
Did you see this in all that output in post #154 and is it anything I need?

jwill1515@jwill1515-laptop:~/Desktop$ sudo ./connect
sudo: ./connect: command not found
jwill1515@jwill1515-laptop:~/Desktop$ sudo itfchg /dev/sdc
sudo: itfchg: command not found
jwill1515@jwill1515-laptop:~/Desktop$ connect
The program 'connect' is currently not installed. You can install it by typing:
sudo apt-get install connect-proxy
bash: connect: command not found
jwill1515@jwill1515-laptop:~/Desktop$ sudo apt-get install connect-proxy
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package connect-proxy

---

### Post by jwill1515 on 2008-02-14
Thank you very much yellowbread. That program of yours seemed to have done the trick. Will I have to go through all this every time? The file of your program is now on my desktop along with an icon of changemode. Do I need to keep those files anymore?

---

### Post by yellowbread on 2008-02-14
You don't really need that stuff. By the looks of things, the programs from franklin still will not run, but you have the mode of the modem changed, and wvdialconf recognizes the modem, so editing wvdial.conf as outlined above and running wvdial should get you online.

---

### Post by jwill1515 on 2008-02-14
Great! I'll give it a shot this evening when I get home and post back. When I click on the connection icon on the taskbar it now has some kind of ppp menu option to connect or disconnect and there is info for the modem (phone number, etc.) in the optional manual configure window that pops up (third option down. I can give you more details later. This is just from recollection).

---

### Post by yellowbread on 2008-02-14
> **jwill1515 said:**
> Thank you very much yellowbread. That program of yours seemed to have done the trick. Will I have to go through all this every time? The file of your program is now on my desktop along with an icon of changemode. Do I need to keep those files anymore?

You are welcome. Thanks to you also. Your patience and determination are impressive. Many people would have given up long ago and nobody would have learned anywhere near as much.

Yes, you should probably keep the changemode program. I keep it in my home directory so that all I have to do to change into modem mode is sudo ./changemode. The modem defaults to data mode every time it is plugged in, so until you get itfchg or connect from franklin working (spiderbatdad has given you some ideas on that) you will need changemode to change it back into modem mode. You don't need the file with the source code anymore.

You will not have to go through most of this every time you connect. If the modem is still in modem mode, wvdial is all you will have to do. If it is not in modem mode, you will have to do sudo ./changemode first. On rare occasions, the changemode program will give the message "Modem not found.", which just means its not listed in /proc/scsi/sg/device_strs. Then you will have to unplug the device, reinsert it, and wait a few seconds for it to be recognized before those two commands.

---

### Post by jwill1515 on 2008-02-14
I couldn't have done it without everyone's kind help and patience, as I have only been exposed to Ubuntu for about a month. I have been impressed with the amount of Ubuntu support from everyone and all the info in the forums. I'll probably need some more help getting drivers and anything else I might need. We'll cross that bridge when we get there.

---

### Post by jwill1515 on 2008-02-14
Yes, I'm in!

sudo ./changemode
sudo wvdial

I can't thank all of you enough. i can't believe you hung in there with me.

Anything i need to do to finish my insallation?

---

### Post by yellowbread on 2008-02-14
You shouldn't need anything else unless you get sick of using wvdial. I find it annoying that I have to have the open terminal while I'm connected with wvdial. Gnome-ppp and kppp are reasonable alternatives.

---

### Post by jwill1515 on 2008-02-14
Forgive me but what are Gnome-ppp and kppp and where can I get them? I'm dowloading 187 updates right now. System/Administation/Update Manager. After that I'm going to run Synaptic Package Manager.

---

### Post by spiderbatdad on 2008-02-14
omg. you win the persistent-man-of-the-year award. Thanks for sticking with this project. I learned quite a bit myself. Gnome-ppp and kppp are both graphical frontends for wvdial. If you use either you may have to make sure they don't write semicolons into /etc/wvdial.conf, especially gnome-ppp. There is a patched version of gnome-ppp you could find by searching the web. It is called gnome-pppfixedforgutsy....I can't vouch for it, as it had a hard time with wvdial. Other wise gnome-ppp and kppp are both in synaptic. Back-up your working /etc/wvdial.conf in case they screw it up. 

Regards, and great work.

---

### Post by jwill1515 on 2008-02-14
What do I do in Synaptic Packade Manager?

---

### Post by spiderbatdad on 2008-02-14
You can use the search filter at the top to help narrow the list, but you need to have an idea of the package name, or its use, for seacrhing. Or you scroll through the list till you find what you want. You check the box, choose mark for installation,  then hit the apply icon at the top of the window.

---

### Post by oilchangeguy on 2008-02-14
just a thought. if it worked in 7.04, there was no real reason to switch to 7.10. just re-install 7.04 and be happy.

---

### Post by spiderbatdad on 2008-02-14
You should mark this thread solved, using the thread tools near the top, and post new threads for future questions.:)

---

### Post by yellowbread on 2008-02-14
> **oilchangeguy said:**
> just a thought. if it worked in 7.04, there was no real reason to switch to 7.10. just re-install 7.04 and be happy.

What's the fun in that?

---

### Post by jwill1515 on 2008-02-14
How come I can't access the files from the Vista part of the computer? There use to be an icon on the desktop that has disappeared and no sign of them in file system. I used to be able to access them.

---

### Post by rkd on 2008-02-14
It's probably something simple.

Run these commands in a Terminal, post the output, and we'll look to see what is wrong.```
sudo fdisk -l
mount
cat /etc/fstab
ls -l /media
```

---

### Post by jwill1515 on 2008-02-14
Thanks rkd,

jwill1515@jwill1515-laptop:~$ sudo fdisk -l
[sudo] password for jwill1515:
Sorry, try again.
[sudo] password for jwill1515:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a48f7e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10543    84686193+   7  HPFS/NTFS
/dev/sda2           13731       14593     6932047+   7  HPFS/NTFS
/dev/sda3           10544       10665      979965   83  Linux
/dev/sda4           10666       13730    24619612+   5  Extended
/dev/sda5           10666       10908     1951866   82  Linux swap / Solaris
/dev/sda6           10909       13730    22667683+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 69 MB, 69206528 bytes
3 heads, 45 sectors/track, 1001 cylinders
Units = cylinders of 135 * 512 = 69120 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     5763970    14219597   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(5763969, 2, 4)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(14219596, 1, 34)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     1249553    15590502   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(1249552, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(15590501, 2, 37)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?    13850974    28191924   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(13850973, 2, 21)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(28191923, 1, 7)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1    26942419  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(26942418, 1, 21)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
jwill1515@jwill1515-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /boot type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb on /media/CDU680_UMSD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdb on /media/CDU680_UMSD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
jwill1515@jwill1515-laptop:~$ cat etc/fstab
cat: etc/fstab: No such file or directory
jwill1515@jwill1515-laptop:~$ ls -l /media
total 28
lrwxrwxrwx 1 root      root     6 2008-02-05 15:37 cdrom -> cdrom0
drwxr-xr-x 2 root      root  4096 2008-02-05 15:37 cdrom0
drwx------ 7 jwill1515 root 16384 1969-12-31 19:00 CDU680_UMSD
drwxr-xr-x 2 root      root  4096 2008-02-05 15:37 sda1
drwxr-xr-x 2 root      root  4096 2008-02-05 15:37 sda2
jwill1515@jwill1515-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=d4b07de9-ca56-4acf-9230-448cdd9f3537 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=50960093-ddbc-4578-9383-43045ae536f3 /boot ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=2C68346B683435C4 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=2C88743C8874071C /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=3098c36d-21eb-4a63-a625-09c298980835 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-14
This might interest you. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jwill1515 on 2008-02-14
GNU nano 2.0.6              File: /etc/fstab                        Modified  

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=d4b07de9-ca56-4acf-9230-448cdd9f3537 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=50960093-ddbc-4578-9383-43045ae536f3 /boot ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=2C68346B683435C4 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=2C88743C8874071C /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=3098c36d-21eb-4a63-a625-09c298980835 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

                               [ Read 18 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by spiderbatdad on 2008-02-14
you should now ```
sudo umount /dev/sda*
sudo mount -a
```

If that doesn't do it. try a reboot. Looks like you should then have read write access to your windows partition.


EDIT: Looks like you may need to add  0  0 to the end of the partition line, so it would look like this:  

     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

---

### Post by rkd on 2008-02-14
Do you know what is going on with that disk sdb? 69 MB -- megabytes, not gigabytes -- is really small. What do you think is on it? As you can see, fdisk thinks it isn't in good shape.

I'll assume that the Vista files are on /dev/sda1 and /dev/sda2.

Let's try mount commands matching what fstab shows to see whether we get any error messages. In a Terminal, do```
sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  -U 2C68346B683435C4  /media/sda1
sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  -U 2C88743C8874071C  /media/sda2
```
Don't try to type those long commands -- use your mouse to highlight the command in this post, go to the Edit menu and select Copy, then click in the Terminal window and go to its Edit menu and select Paste, then push the Enter key.

Post any error messages you get, and check to see whether the disks are mounted.

If those commands don't get the partitions mounted, try these commands in a Terminal
```
sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  /dev/sda1  /media/sda1
sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  /dev/sda2  /media/sda2
```
Post any error messages you get, and check to see whether the disks are mounted.

---

### Post by jwill1515 on 2008-02-15
Thank you. I'll give that a try this evening and post back. The gentlemen at the Linux User Group meeting set the drive up that way when we installed. I forget the details. I was uncomfortable installing Ubuntu and partitioning the drive on my own. I ran into something else. While I was browsing last evening I hit a link to a video clip. A program popped up but no video ever appeared. Is there something else that I need?

---

### Post by yellowbread on 2008-02-15
rkd, the 69 MB disk is the cdu680.

jwill1515, there's a package called ubuntu-restricted-extras in synaptic that includes the flash-player plugin, which is probably what is missing. If you can't find it, look under System>Administration>Software Sources and on the first tab, make sure main, universe, multiverse, and restricted are all checked.

---

### Post by jwill1515 on 2008-02-15
69 MD? Is that,

Disk /dev/sdb: 69 MB, 69206528 bytes
3 heads, 45 sectors/track, 1001 cylinders
Units = cylinders of 135 * 512 = 69120 bytes
Disk identifier: 0x6f20736b

---

### Post by jwill1515 on 2008-02-15
Thank you yellowbread. You have been a big help. A question if I may. What's the difference between Ubuntu and Kubuntu? Is it just looks? Most of the people at the user group are using Kubuntu.

---

### Post by jwill1515 on 2008-02-15
Oh, by the way the CDU-680 is working great and connects right up with Gnome-ppp.

---

### Post by yellowbread on 2008-02-15
I don't use kubuntu, all I know is that it uses KDE instead of gnome. Do a google search for kubuntu and you'll get lots of information.

---

### Post by jwill1515 on 2008-02-15
What's the difference between KDE and Gnome?

---

### Post by yellowbread on 2008-02-15
Glad to hear the CDU680 is finally working. Did rkd's instructions get you windows partitions mounted?

---

### Post by yellowbread on 2008-02-15
I don't know much about KDE so I couldn't really say how its different.

---

### Post by jwill1515 on 2008-02-15
I didn't have any luck mounting the partition last evening and haven't had a chance to try rkd's instructions yet. It will be this evening before I can get to it.

---

### Post by rkd on 2008-02-15
yellowbread:

Thanks, I didn't notice that /dev/sdb was the CDU680. Is it giving fdisk fits because it has been switched to data modem mode?

jwill1515: 

I don't yet know enough to know how to describe the difference between Gnome and KDE. One obvious difference is the appearance of the desktop, but it goes further than that. Each of Gnome and KDE has a sort of software framework within which the various components of the desktop applications interact with each other. That part I still know very little about. I think it has to do with how they fit into menus, store their configurations, how the file browser knows when devices are mounted and unmounted, and more things like that.  However, I'm told that you can install a KDE application into a Gnome system (and the other way around, too), and the foreign application will work acceptably. I don't quite understand how that works.

The software underneath the desktop is the same on both systems. The Linux kernel is the same, all the device drivers, filesystems, package manager, the command line shells, the X window system, and many applications such as firefox, gimp, etc. -- all of those are identical.  Gnome and KDE (and several other desktop environments) are built on top of that common foundation.

So that's what I understand so far about Gnome and KDE. I haven't tried any KDE yet, so I know very little details about it.

Back to your disk mounting problem: Whenever you get a chance to try the mount commands is fine, tell us what happened when you get to it. I'm sure it will be a much easier problem to solve than the data modem problem was!

---

### Post by yellowbread on 2008-02-15
The CDU680 gets the same results with fdisk, no matter what mode its in. It seems to work fine as a data device regardless .

---

### Post by jwill1515 on 2008-02-15
Here you go...

jwill1515@jwill1515-laptop:~$ sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  -U 2C68346B683435C4  /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
jwill1515@jwill1515-laptop:~$ sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  -U 2C88743C8874071C  /media/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
jwill1515@jwill1515-laptop:~$ sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  /dev/sda1  /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
jwill1515@jwill1515-laptop:~$ sudo mount  -t ntfs-3g  -o defaults,locale=en_US.UTF-8  /dev/sda2  /media/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-15
Hey jwill1515, I'm no expert on mounting either:popcorn: But I did recently read an article in the ubuntu planet about Disk Manager. I installed it and it seems to work well for my limited needs. It is a graphical App that locates itself System>>Administration. It makes the mounting of partitions and other devices very user friendly.  Here's a link to it.  [http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

---

### Post by jwill1515 on 2008-02-15
jwill1515@jwill1515-laptop:~$ sudo umount /dev/sda*
umount: /dev/sda: not mounted
umount: /dev/sda1: not mounted
umount: /dev/sda2: not mounted
umount: /boot: device is busy
umount: /boot: device is busy
umount: /dev/sda4: not mounted
umount: /dev/sda5: not mounted
umount: /: device is busy
umount: /: device is busy
jwill1515@jwill1515-laptop:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
jwill1515@jwill1515-laptop:~$

---

### Post by jwill1515 on 2008-02-15
Thanks spiderbatdad. So do I download the one for feisty? Do I open with GDebi or save to disk? I haven't done this yet


EDIT: Looks like you may need to add 0 0 to the end of the partition line, so it would look like this:

/media/<mount point> ntfs-3g defaults,locale=en_US.utf8 0 0

How do I go about that again?

---

### Post by spiderbatdad on 2008-02-15
I probably used the source. But, looking in synaptic package manger...I see it is there, so that is probably the best way to get it. It requires ntfs-3g, but you already have that I believe.

---

### Post by jwill1515 on 2008-02-15
So do I open the disk manager with the GDebi Package Installer or save it to disk?

---

### Post by spiderbatdad on 2008-02-15
Just go to synaptic package manager...mark it for installation...and apply it.

---

### Post by jwill1515 on 2008-02-15
Thank you spiderbatdad. You're a busy guy tonight. I see you and yellowbread are helping someone else with a CDU-680. Mine's working great now with Gnome-ppp. Did you say there was a way to get the modem working without doing the changemode all the time?

---

### Post by spiderbatdad on 2008-02-15
> **jwill1515 said:**
> Thank you spiderbatdad. You're a busy guy tonight. I see you and yellowbread are helping someone else with a CDU-680. Mine's working great now with Gnome-ppp. Did you say there was a way to get the modem working without doing the changemode all the time?

Not I. Must be yellowbread said that...I think you only need to run it after you restart. Theres probably a way to add ./changemode to startup options so that it runs automatically when you log in...or add it to init.d, but that is a question for yellowbread...you might be able to send him a private message to see what he thinks. 

To try to add it graphically  System>>Preferences>>Sessions...click add...name changemode...command> use browse to navigate to the program in your home directory (or Desktop) wherever the program is. Next go to the sessions options tab and select "Remember Currently Running Applications."   This sessions manager can be quirky. Sometimes it takes a few tries. You may also be able (after reboot) to set a startup order to 90 ( to make sure everything else is loaded before it runs) this is done under the "Current Sessions" in the sessions manager.

---

### Post by jwill1515 on 2008-02-15
No luck with accessing the Vista partition. Disk Manager was already loaded on computer. I checked the box for NTFS policy enable write support. Nothing. It says there are 4 partitions (I believe there a five - that's what my grub menu says) in use and configured.

---

### Post by spiderbatdad on 2008-02-15
Hmmm. Bummer. All I know about mounting comes from that how-to by psychocats: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

And this post: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=378426&page=36](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=378426&page=36) by Bohdi.zazen.

It seems it one of your posts there was a problem where windows was not shut down cleanly. Make sure you always do that.  My recommendation is throw windows out the window, and make due with Linux...but that's just me.:)  Many people need certain windows apps.

---

### Post by jwill1515 on 2008-02-15
Ah! There it is. Great suggestion spiderbatdad. I must have shut down Vista in hibernation mode. Will Ubuntu run files from Vista? .wma or whatever extension media center uses?

---

### Post by spiderbatdad on 2008-02-15
.wma runs fine. if you want to run a .exe that's a whole other ball of wax called wine (wine is not an emulator). It runs some windows programs...game most commonly. I don't use it. I stick to open source. 

For .wma you will probably need codecs for totem (or whatever player). Totem will prompt you to install them, and pretty much do it for you. There is an open source solution to nearly every computing issue, sometimes the solutions require a bit of work (as you know!) But development is steady.

---

### Post by yellowbread on 2008-02-15
You only need to use the changemode program when the modem is not in modem mode. This happens whenever you do a cold boot, or the modem has been unplugged. Gnome-ppp will give you a message that it cannot open the modem whenever this is the case. Other than that, gnome-ppp is all you need. On rare occasions, although the modem was in modem mode, gnome-ppp could not open it. Reinserting it and running ./changemode fixed that.

By the way, gnome-ppp on Gutsy used to have this problem where it would connect, but the gui would hang with the message "Connecting..." or something like that. This was fixed on Hardy alpha 4. Have you had any problem with it?

---

### Post by jwill1515 on 2008-02-15
Yes, I got it now. Everything seems to be working well. I can access and play my music and movie files. Do you know if Ubuntu can run AutoCAD or SolidWorks?  I'll make a new post if I run into anything else. Thanks for all your help. Enjoy the rest of your evening.

---

### Post by spiderbatdad on 2008-02-15
[http://architectafrica.com/bin0/news200411111_wine.html](http://architectafrica.com/bin0/news200411111_wine.html)

---

### Post by jwill1515 on 2008-02-15
Interesting. Thanks.

---

### Post by jwill1515 on 2008-02-15
One more thing...

How can I access the webcam built into my computer?

---

### Post by rkd on 2008-02-15
About your NTFS disks: spiderbatdad pointed out that the error message said the problem was that the disks weren't shut down cleanly in Vista.  Did you try to boot Vista then shut down normally, then boot Ubuntu again? If not, that should be all you need to do to bring up the NTFS disks in Ubuntu (unless using Disk Manager messed up something).

If you try that remedy and it doesn't work, post your current fstab and the output from the mount commands again.

It probably would be a good idea for you to start new threads for unrelated questions. For one thing, you'd be able to use a thread title that reflected the new question. That would attract the attention of people who know about the new topic. For another, someone who wanted to help with the new question wouldn't have to page through 200 posts about the modem before getting to the new question.

---

### Post by handitard on 2008-03-26
> **jwill1515 said:**
> I got it working in Feisty no problem using the sudo ./connect command in the terminal program. I contacted Franklin and the gentleman told me to,

1. copy to desktop all files except 'itfchg'
2. open terminal and type "sudo ./itfchg/dev sd?
"?" being where the CDU-680 is located. in my case it was sdb, it may be sda or sdb
3. in terminal run execute.sh and modem will activate

I followed the above direction with no luck. I tried sda, sdb and sdc.
How do I tell what the sd? letter is and where the modem is located? I plug it in the front right USB slot on my HP Pavilion dv9205us. The printer is plugged in the rear right USB port directly in front of the power cord and I have a chill mat plugged in one of the left USB ports. There are four ports all together. I am new to Linux and this is all pretty confusing to me. I read some of the posts and I was getting more confused. I can't be that hard to get this modem working in 7.10. It worked no problem in 7.04. I must be doing something wrong. I would appreciate any help or advice.

it might help if you plugged it in!:lolflag:

---

