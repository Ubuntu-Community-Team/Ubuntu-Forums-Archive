---
title: "In a real mess with Real Player"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by keithk50 on 2007-02-28
Hello,   I have tried to install real player several times onto my laptop without success. Being new to Ubuntu (1 week) I think I've managed to really mess things up trying to install the RealPlayer10GOLD.bin file. Have downloaded the file 3 times now!  When I type "chmod a+x RealPlayer10GOLD.bin into Terminal I get:
keith@keith-laptop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
keith@keith-laptop:~$

I have ticked the Execute box within the permissions of the bin file but it will not open when double clicked.   Nothing happens.   When I uncheck the Execute box the file opens with the error message:   "Could not open RealPlayer10GOLD.bin.   Archive type not supported".
I have obviously messed the whole thing up while trying to install several times!   Is there any way clearing the way through in order to install Real Player from scratch?  Any guidance and help would be appreciated.   Thanks.

---

### Post by taurus on 2007-02-28
```
cd ~/Desktop
chmod a+x RealPlayer10GOLD.bin
```

---

### Post by Maestro23 on 2007-02-28
> **keithk50 said:**
> Hello,   I have tried to install real player several times onto my laptop without success. Being new to Ubuntu (1 week) I think I've managed to really mess things up trying to install the RealPlayer10GOLD.bin file. Have downloaded the file 3 times now!  When I type "chmod a+x RealPlayer10GOLD.bin into Terminal I get:
keith@keith-laptop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
keith@keith-laptop:~$

I have ticked the Execute box within the permissions of the bin file but it will not open when double clicked.   Nothing happens.   When I uncheck the Execute box the file opens with the error message:   "Could not open RealPlayer10GOLD.bin.   Archive type not supported".
I have obviously messed the whole thing up while trying to install several times!   Is there any way clearing the way through in order to install Real Player from scratch?  Any guidance and help would be appreciated.   Thanks.

Where did you download the file to?  Your Desktop? If so:

> cd /home/username/Desktop

ls (shows what is on your Desktop)

Then:

sudo chmod +x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin


---

### Post by keithk50 on 2007-02-28
Thanks for the really quick replies.   Entered the code given by Taurus and Terminal inserted some info and finally stated that Real Player was installed.   I then noticed a new folder on the desktop labeled Real Player.   This has several files in it.
I then went to the BBC website and clicked on a video preview.   It stated that I needed the plugin!.   When I clicked on Stand alone Player it tried to open up in Totem then gave an error message.
Once installed is Real Player put into the Applications menu?   Looked but not there.   Am I doing something wrong?   Have not entered the codes mentioned in Maestro23's post, Should I?   Thanks again.

---

### Post by arochester on 2007-02-28
The BBC has an advice page "Advice for Unix/Linux users" at [http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml) . OK it says Radio and Audio but take my word it works for video as well. The trick is: "The files nphelix.so and nphelix.xpt must be in the browser's plugins directory for Opera, Firefox and Mozilla"

Yes, I can watch BBC videos

---

### Post by nudnik on 2007-02-28
> **keithk50 said:**
> Thanks for the really quick replies.   Entered the code given by Taurus and Terminal inserted some info and finally stated that Real Player was installed.   I then noticed a new folder on the desktop labeled Real Player.   This has several files in it.
I then went to the BBC website and clicked on a video preview.   It stated that I needed the plugin!.   When I clicked on Stand alone Player it tried to open up in Totem then gave an error message.
Once installed is Real Player put into the Applications menu?   Looked but not there.   Am I doing something wrong?   Have not entered the codes mentioned in Maestro23's post, Should I?   Thanks again.

Delete the folder using the command line and reinstall the player to the /usr/bin directory. There should be a prompt which appears during the command line installation which allows you to do this. 

At the moment the file is just sitting on your desktop, which explains why its not linked properly.

---

### Post by keithk50 on 2007-02-28
Thanks for reply nudnik.  Excuse my ignorance but could you please explain to me how to delete the folder (code) in the command line and delete the folder.  As a novice the terminal is a 'dark and mysterious' place to me.   Sorry.  Any further help appreciated.

---

### Post by Mark Gillis on 2007-02-28
Thanks for the How-to, I also could not get Real Player to work until I got it into /usr/bin. Remember that you have to work in the root directory to get it to work ( or at least that is the way I did it)

---

### Post by keithk50 on 2007-02-28
I know I am being a pest, and I am really grateful for the help on this problem, but I am completly at a loss as how to carry out this:

"Delete the folder using the command line and reinstall the player to the /usr/bin directory. There should be a prompt which appears during the command line installation which allows you to do this.

At the moment the file is just sitting on your desktop, which explains why its not linked properly."

I have spent some time reading several help topics for terminal commands but it really is not easy for a beginner and I am afraid of creating chaos in my lovely new Ubuntu setup!

---

### Post by Mark Gillis on 2007-03-01
Hi Kieth! I too am a newbie but managed to get Real Player up and running. There should be a raw file on your desk as well as the folder for Real Player. Put the folder Real Player in the trash...Its not going to do you any good. (I know, I tried to get it working that way too!) As long as your files are on the Desktop they are of no use. What we have to do is get them down into the guts of the machine where the operating system can reference them. First step is to get into the command line. I know it is kinda scary for windows duds like me to fish in a black terminal box, but it turns out you are usually OK- after all all you can do is mess up your installation, and you know how to do that again right? ( I've only done it twice now!):)  Once you are there type in dir and hit return. You are looking for "Desktop" if this is listed in front of you, type cd Desktop and that will put you into the Desktop directory. The commands will not work to activate the files if you are not in Desktop! The guys before me have shown you a few ways to get into Desktop, but you must be able to move your self around the innards of your computer to do this. Once in Desktop:
Then:

sudo chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

Will get the files where they should be and not on your Desktop. You will have to give your password (admin) to place Real Player in where it need to be. In my computer this kicked off an automatic routine where I got updates in Firefox and additional links in the system, but now Real Player works were ever I need it to. Just make sure you are able to get any updates from the net when you put it together.:guitar: 

WARNING!! This advice was given by a relative newbie who spent until 2 am compiling banshee with unauthorized plugins. It may or may not be completely correct, its just hard to remember what I did yesterday... When in doubt listen to the experts on this forum!

---

### Post by keithk50 on 2007-03-04
Hi Mark,   Thanks for your interest.   Well done on getting Real Player to work, I nearly gave up but thought what the heck, if I can install a whole operating system dont let one small programme beat you.  I even installed MPlayer using Automix2 (very good app) and that plays the media I needed (mainly from the BBC web site).
Automix started to install Real Player but also hit a problem.   Never mind, I shall keep on trying.    Thanks again for your interest and advice.     Keith

---

