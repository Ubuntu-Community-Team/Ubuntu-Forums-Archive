---
title: "[SOLVED] Wireless USB adapter driver"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Cerins on 2007-12-31
hi evryone,
I'm new to Ubuntu, and i have major problems making my USB wireless adaptor to work...
I tryed to use "ndiswrapper" to make the xp driver that i got with the disk work, but im not quite sure wt im doing :P
So yh... its 2 days im trying to solve this and... I NEED HELP!!!
Info:
Wireless USB adapter: A02-UP-W54 released by Atlantis Land
drivers are in the cd, but only for Win 98,ME and XP

thank you... really need help...

---

### Post by gigaferz on 2007-12-31
what did you do?

why dont you type ina terminal window "ndiswrapper -l"

---

### Post by Cerins on 2007-12-31
id be glad if u could tell me wt to do plz...like the all process .. like wt version of ndiswapper i have to use..  im not very experienced ...lol

---

### Post by gigaferz on 2007-12-31
ok, lets do this, 

first copy the folder with the xp drivers to your desktop or home folder

then go to System ->Administration ->Synaptic package manager
  and search for ndiswrapper  you need ndiswrappet-common and ndiswrapper-utils and install them

---

### Post by gigaferz on 2007-12-31
well, i need to run an erand, dont give up...

 after installing ndiswrapper

open a terminal window

then go to the folder where your wireless drivers are, 

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

go to the installation section where it says "If you already have your device working in Windows"   keep reading , 

 also when you are in a terminal window you will need the following commands
"ls"               shows you what is in that directory files and folders
"cd"              change directory
                 so if you want to change to a folder named pictures type "cd pictures" then                             enter, and if you want to go up type "cd .." then enter

  ill check the thread later

---

### Post by Cerins on 2008-01-01
ok i  did most of wt u told me to... though when i read the instructions, it tells me to "open the device menager and find ...." 
where is the device menager?

---

### Post by Cerins on 2008-01-01
plz anyone... i need to get my wireless thing working...

---

### Post by gigaferz on 2008-01-01
hello! youre back, do you have a yahoo or msn google or myspace messenger account ?
are you using another computer to get internet or is it the same one but using a wired connection?

Ignore that part, 

as long as you have installed ndiswrapper and you have the xp drivers you are fine.

 just go in the folder with the drivers  , and type 
ndiswrapper -i yourdrivername.inf   replace that with the name of your driver, 

then type ndiswrapper -l you should see (like in the installation page) device present and driver present message

---

### Post by Cerins on 2008-01-01
its kinda complicated... using another computer... i seariously need help with this... canu tellm me wt to do next pls... btw i haf no yhaoo and my msn is not working... sorry bout that...

---

### Post by gigaferz on 2008-01-01
ok, do you have a terminal window open?

applications ->accesories->terminal

---

### Post by Cerins on 2008-01-01
yup

---

### Post by gigaferz on 2008-01-01
type:
 ndiswrapper -l

what does it say?
you can also copy and paste

make a fake account with google or yahoo  they both have a messenger system and does not requiere any download or installation..itll be easier

---

### Post by Cerins on 2008-01-01
it sais "SiS163u invalid driver"..... i guess my previous attempts were ---useless..lol

---

### Post by gigaferz on 2008-01-01
where did you get that driver?
What about the device, what does it say?

---

### Post by Cerins on 2008-01-01
the installation cd of my adapter
doesnt say nething bout the device

---

### Post by gigaferz on 2008-01-01
type in the terminal 
dmesg
pay attention to the last lines, 
now unplug the device and then plug it back and type demsg again and look at the last lines
put here the before and after output
dont copy and paste the whole dmesg output, just the last 5 lines

---

### Post by Cerins on 2008-01-01
ok it did change... b4 it said link not ready,now says configuration chosen from 1 choice... wts next?

---

### Post by gigaferz on 2008-01-01
ok, can you  copy and paste here  the last lines form dmesg?

can you post the result of : lsusb

---

### Post by gigaferz on 2008-01-01
can you get wired internet on that computer?

since you unplugged the usb card and plugged it back try again typing ndiswrapper -l

---

### Post by Cerins on 2008-01-02
last 5 lines of demsg

[  497.316000] UDF-fs: No VRS found 
[  497.344000] ISO 9660 Extensions: Microsoft Joliet Level 1 
[  497.348000] ISOFS: changing to secondary root 
[  614.020000] UDF-fs: No VRS found 
[  614.060000] ISO 9660 Extensions: Microsoft Joliet Level 3 
[  614.100000] ISO 9660 Extensions: RRIP_1991A 

result of lsusb:

us 005 Device 003: ID 0457:0163 Silicon Integrated Systems Corp.  
Bus 005 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 003: ID 0851:1542 Macronix International Co., Ltd  
Bus 001 Device 001: ID 0000:0000   

here u go... nha wired connection i cant get coz the computer with ubuntu on is too far away for the wire.. so yh... when i try to install the driver now it says 

couldn't create etc/ ndiswrapper/ SiS163u permission denied at /usr/sbin/ndiswrapper - 1.9 line 152.

soo.. am i a lost case? lol

---

### Post by Cerins on 2008-01-02
i reinstallled ubuntu 7.10 and ndiswrapper 1.9.... can anyone tell me how to get this driverto work plz... i cant haf a computer wid no internet!

---

### Post by Cerins on 2008-01-02
ppl please help me out!!!

---

### Post by anewguy on 2008-01-02
I'm going to try to help you, but I make no promises.  If you installed ndiswrapper I'm going to assume you also installed the utilities as mentioned previously, if not - install those first.

First, go to a terminal window (Applications/Accessories/Terminal)

Type:

sudo ndiswrapper -l

Does it return anything or just back to the command line?

If it returns something about a driver installed, do this:

sudo ndiswrapper -r   xxxxxxxx  <- where xxxxxxxx is the name that showed from the list command above

If needed, repeat the above 2 steps until the list command (-l) returns nothing.


Now, open your driver CD and copy the .inf and .sys files from it (may be in a folder called driver or drivers) to your desktop (you can click and drag them).

Once you have done all of this, post back here and we'll go from there.:)

---

### Post by Cerins on 2008-01-03
ok when i type
 
sudo ndiswrapper -l

its goes 

[sudo] password user:

and i guess i haf to insert my password, but it doesnt let me typr anything... im not quite sure... i got the .inf and .sys files on my desktop... your turn lol

---

### Post by anewguy on 2008-01-03
The password is indeed just your password, and it doesn't echo on the screen so it appears not to be doing anything, but just type it in anyway and when done press enter.

Please post back with the result of that.:)

I'll probably be up for a little while yet as I can't get to sleep even though I need to be up in 3 hours.

---

### Post by Cerins on 2008-01-03
ok  i typed in the password n pressed enter, and now it doesnt return nething so i guess i got that ryt lol next step then

---

### Post by anewguy on 2008-01-03
Okay, now we are ready for the next step:

Again, in a terminal window (Applications/Accessories/Terminal):


sudo ndiswrapper -i  ~/Desktop/xxxxxxxx.inf

where:
   -  it's lower case "I" for "install"
   - substitue xxxxxxxx.inf with the name of your driver inf file (include the .inf)

then:

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m


If you do these in sequence in the same terminal window, the "sudo" (stands for super user do) should only prompt you for your password once (at least that's how it works for me).

When you've done all of that, then check for the network icon on your top bar.  Click it, find your network, and click the dot and connect.  If you need a WEP or WPA password it will prompt for that.

If a WEP or WPA password was needed, the system stores in on a logical "keyring".  It will probably ask you for a keyring password - try just putting in your log in password.  If a package called "PAM" is installed (I think it might be by default in 7.10) then each time you restart your PC or try to access the network again after a disconnect it will automatically connect if your keyring password is the same as your log in password.

Post back with any questions/problems/results.:)

---

### Post by Cerins on 2008-01-04
dude this thing really doesnt wanna work... ill post my result.. it said my driver was already installed, and then after i did all wt u said that it was invalid... i think i should go deleate the previous driver file coz i think that the previous installation was a bit screwed up...

cerins@rubuntu:~$ sudo ndiswrapper -i ~/Desktop/SiS163u.INF

driver sis163u is already installed

cerins@rubuntu:~$ sudo depmod -a

cerins@rubuntu:~$ sudo modprobe ndiswrapper

cerins@rubuntu:~$ sudo ndiswrapper -m

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

cerins@rubuntu:~$ sudo ndiswrapper -l

sis163u : invalid driver!

cmon man gimme some last tips i feel it we r so close to solve this problem! lol

---

### Post by zipperback on 2008-01-04
I use wicd for the network manager and it makes the network management of my network connections a really simple task.

Here is the URL for wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Works great!

- zipperback
:popcorn:

---

### Post by Cerins on 2008-01-04
would that solve the problem i haf wid my driver though? coz thats why my wifi is not workin on my computer... its the usb...

---

### Post by Cerins on 2008-01-04
ok i tried to disinstall the driver, but it says  that there is no driver there... so i try to install it... and it says there is already a driver... and then it tll me is invalid with ndiswrapper -l... how can i install this drivr properly?

---

### Post by anewguy on 2008-01-04
If ndiswrapper is saying the driver is already installed, what does it return when you do ndiswrapper -l (lower case "L") to list what it has already?

Given what you are saying, I would try the following first:

sudo ndiswrapper -r SiS163u  (notice there is no .inf or anything)

If that fails, be sure to match the case EXACTLY as it is shown in ndiswrapper -l

then try

sudo ndiswrapper -l (lower case "L") 

If ANYTHING is returned above, you must repeat the sudo ndiswrapper -r with each name returned until the list is blank.  All of this MUST be done and an empty list returned before you can try to install again.

It is very important to match the case and exact spelling of anything involved, including your driver file - is it really capital letters or is it lower case?  Remember - this is not Windows so case DOES matter.

You must get to a clean starting point - nothing being returned in the list - before you can start installing.  Case is very important, as is the path to the file.  In fact, to eliminate one potential source of error, when you first get in the terminal window but before you start doing any commands, change your working directory to the desktop as follows:

cd Desktop


Then when you are issuing the install command, leave off the path and just use the file name. 

The type of error you are describing usually is the result of the path or the file name being incorrect - ndiswrapper says "okay, I installed it" when in fact (at least in my experience) it did nothing.  You have to remove the erroneous stuff and start with a clean list.

After that, if problems continue, you may want to try one of the other tools mentioned.

---

### Post by anewguy on 2008-01-05
One more thought - are you using 32-bit Ubuntu or did you install the 64-bit version?  I think the driver is 32-bit, and I'm not sure that will work if you installed 64-bit Ubuntu.:)

---

### Post by Cerins on 2008-01-05
hey man... i think we r almost there... though there is one more thing.. lol this thing is endless aha...

look at wt it tells me

cerins@rubuntu:~$ sudo ndiswrapper -r sis163u

cerins@rubuntu:~$ sudo ndiswrapper -i SiS163u.inf
installing sis163u ...
couldn't open SiS163u.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.

ok just to give u a quck summary ( hope its the last one!) i so the folder being deleated, so there is no old stuff on the computer... after it failed the installation... so thers nothing corrupter or nething like that... so plz one last time man... help me out :lolflag:

---

### Post by anewguy on 2008-01-05
Okay, what that is telling you is that ndiswrapper couldn't find the filename you specified - in this case SiS163u.inf.  BUT - there is a reason for that!  Looking at the command prompt on what you posted, you forgot to follow the step to change your default directory to the Desktop (this is where you said you put the driver files).  So, I would guess now you have a "bad" file listed if you do the ndiswrapper -l again.  Remove it as noted in my previous post, then follow that post again beginning where it says to cd Desktop.  Based on what you have posted, your prompt should change to:

cerins@rubuntu:~/Desktop$ 

Then if you do the following to list the directory contents:

ls -al

you should see your .inf and .sys files.  At this point you can continue on with the installation of the driver.


:)

---

### Post by boballen55 on 2008-01-06
Hey man, hope you are making headway, it looks like the other posters have you pretty close.  I just installed Ubuntu 7.10 a little over a week ago and went through this process to get my USB wireless adapter to work and this link explained it all pretty clearly:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573)

If you're patient and follow all the steps just that document might get you through.

Also, like me, I can see that you are very new to the terminal as well, I found this series of posts to be very enlightening to the basics of using the terminal:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Hope that link can explain some of the simpler commands that can be used in the terminal.

Good luck!

---

### Post by Cerins on 2008-01-06
yo peeps! i menaged! the driver is installed and the device is detected !! (yay!) now... ok i now this is realy dumb but how do i configure my wireless connection??? there is only modem and wired... im sure there is a way ...

btw tnx to all of thepeople that have helped me out with this... especially anewguy... tnx alot n hope u can help me out wid this as well

 cheers

---

### Post by boballen55 on 2008-01-06
That help file in my previous post can help you configure your connection.  I'm not sure exactly where you are but I think you should be able to figure it out by looking in the third section (Configuration) of that article.  Don't forget to set it up so that it will automatically load at start up (near end of section 3).

Hope that helps, good luck.

---

### Post by Cerins on 2008-01-06
dude my problem is that when i open the networks, there is no wireless that i can select ... only wired and modem... and i think this is not normal... coz also in the help section of ubuntu it says that there should be an icon with 2 computers one ontop of each other... but i dont haf dat on mine!

---

### Post by gigaferz on 2008-01-06
hey cerins!
good to hear you got it almost working read the link I gave you a while ago, once the device is present and the driver is installed is just a matter of minutes to get it working,  unfortunately  (?) you gotta stay in the command line interface, read carefully  , that is the key, i know is stressing but youre almost there

Basically you need to do:::
Before you load the module, DO NOT FORGET to type depmod -a. If there is no error, continue.

To load the module type modprobe ndiswrapper. If you get no error, the driver should now be loaded. You can verify this by checking the system log produced by dmesg

after this is done

iwlist wlan0 scan    will give you a list of networks (cells) ,check your device id (wlan0,ath0,eth0)

---

### Post by anewguy on 2008-01-06
You will also want to go to System/Administration/Network and see if a section called "Wireless connection" shows.  If so, single click on it then click on "Properties" and be sure the "Roaming Mode Enabled" box is checked.

Also, review my previous post with the detailed instructions - it showed the depmod -a and the modprobe ndiswrapper, and also shows the ndiswrapper -m which you need to do as well.  Don't just stop at the driver installation with ndiswrapper. 

If you didn't do the last 3 above, then your wireless probably won't show when you try to list it with ndiswrapper if you have restarted your machine.  You will need to use ndiswrapper to reinstall the driver then, followed by the depmod, modprobe and finally ndiswrapper -m.:)

---

### Post by Cerins on 2008-01-07
people... im proud to say that... IM WRITING U FROM UBUNTU NOW!!!! ppl u are legendary i swear tnx sooo much... id bet anything Microsoft doznt haf such a good community tnx evryone seariously !

---

### Post by boballen55 on 2008-01-07
Nice Work!  and things do get easier with a little experience.  I experienced some frustration when getting my wireless to work as well but with the help of this great community I made it through,

Good luck in your future endeavors.

---

### Post by gigaferz on 2008-01-08
good to hear that you did it!!
,can you mark this thread as solved?

---

### Post by Cerins on 2008-01-08
sorry guys before marking this as solved i want to ask one more question... how can i get my computer to connect as soon as it turns on? and to reconnect when it disconnects?? im a bit tired of re entering the came codes wvery time i turn on the computer to conect... is there a way?

---

### Post by boballen55 on 2008-01-09
I already told you:

> **boballen55 said:**
> That help file in my previous post can help you configure your connection. ...  Don't forget to set it up so that it will automatically load at start up (near end of section 3).

it may be a simple as:
```
sudo ndiswrapper -m
```

---

