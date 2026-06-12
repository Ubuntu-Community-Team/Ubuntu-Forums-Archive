---
title: "I give up....Dell Inspiron 9400"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by di98mase on 2007-09-02
Let me tell you my story. I have a Piece Of Crap (PC) laptop from Dell. It is a Inspiron 9400 with the awful Microsoft Vista installed. This combination sucks! However, I read about Linux and Ubuntu so I deceided to try the Installation CD on my laptop just to see how it looks. I Downloaded the CD, burned it and try to boot with it. No success, I got a blue screen telling me that I had a problem with the X Server. Fine after browsing the forums I found that it could have something to do with my xorg.conf file which can be manually edited or fixed just by running the sudo dpkg-reconfigure xserver-xorg. Howver even this didnt help, even if I tried it several time with different options. After more browsing I found out that I could edit the xorg.conf file manually which I did. The conclusion I made is that Ubuntu has a problem with my graphics card ATI Mobility Radeon X1400. So  according to a blog I read I had to uncomment two lines in the xorg.conf file. These lines did "download" packages from somewhere on the net as far as I understand. Even with this setting it did not work, and how should it since I guess that I have no Internet connection since the laptop has not booted up yet!? 

However using the new settings in the xorg.conf file gave me new errorrs, now it says that It cant find any monitors (I think) soomething like this was displayed "(EE) VESA(0) : No....."

So a few things I dont understand, How is it possible to download newer drivers etc and use them when I run from a CD? 

Is it possible to get someone elses xorg.conf file and use it during boot e.g. by mounting a usb stick and copy the file to the correct location?

What to do? I am stuck between Vista which is the worst OS I have ever seeen and Unbuntu which does not even boot?

Shall I try a new Linux distribution?

Please any advice would be apreciated.

---

### Post by Zootropo on 2007-09-02
You should have used the alternate CD for installation, to use a text based installation. There you should have selected only 640x480 as available modes.
Once installed, you only have to install the fglrx driver with sudo aptitude install xorg-driver-fglrx

---

### Post by jpsimm on 2007-09-02
> **di98mase said:**
> Let me tell you my story. I have a Piece Of Crap (PC) laptop from Dell. It is a Inspiron 9400 with the awful Microsoft Vista installed. This combination sucks! However, I read about Linux and Ubuntu so I deceided to try the Installation CD on my laptop just to see how it looks. I Downloaded the CD, burned it and try to boot with it. No success, I got a blue screen telling me that I had a problem with the X Server. Fine after browsing the forums I found that it could have something to do with my xorg.conf file which can be manually edited or fixed just by running the sudo dpkg-reconfigure xserver-xorg. Howver even this didnt help, even if I tried it several time with different options. After more browsing I found out that I could edit the xorg.conf file manually which I did. The conclusion I made is that Ubuntu has a problem with my graphics card ATI Mobility Radeon X1400. So  according to a blog I read I had to uncomment two lines in the xorg.conf file. These lines did "download" packages from somewhere on the net as far as I understand. Even with this setting it did not work, and how should it since I guess that I have no Internet connection since the laptop has not booted up yet!? 

However using the new settings in the xorg.conf file gave me new errorrs, now it says that It cant find any monitors (I think) soomething like this was displayed "(EE) VESA(0) : No....."

So a few things I dont understand, How is it possible to download newer drivers etc and use them when I run from a CD? 

Is it possible to get someone elses xorg.conf file and use it during boot e.g. by mounting a usb stick and copy the file to the correct location?

What to do? I am stuck between Vista which is the worst OS I have ever seeen and Unbuntu which does not even boot?

Shall I try a new Linux distribution?

Please any advice would be apreciated.
Send away for a CD of the version you want and do it the easy way...

---

### Post by kellemes on 2007-09-02
You posted a question about this one day ago and giving up already?
This post should have included your /var/log/xorg.conf and your /var/log/Xorg.0.log and every litle detail about your hardware. I could have helped you myself if you had provided this info.

---

### Post by di98mase on 2007-09-02
Well I have spent more or less all my free time during these days to get Ubuntu up and running. I didnt beleive that it should cause me so much "problems". However, I just needed to write off some frustration thats why I wrote this post. 

Ok, good to hear that there are people who can help me. 

The reason why I have not provided you with the details of my files is that I dont know how to save the contents of the Ubunet output e.g. xorg.conf. Since I am booting Ubuntu from the CD...how do I save the output to a file that can be read in Windows later? This is also one of the issues that makes this so frustrating. I have to boot Windows and search the forums. reboot the laptop and try boot Ubuntu and when I encouonter problems WRITE down on a paper the messages I get, then go back to Windows and search...well this is often to much info to write down on a paper...this is why I am a bit lazy about providing exact details. Could this be done in a differnet way?

Also what is the alternate CD? Also what version do I want? And what is the easy way? A thought that downloading the latest version and burning a CD WAS/IS the easiest way??

/di98

---

### Post by puccaso on 2007-09-02
on my 9400, i have an ATi graphics card

the one thing that doesnt work for me
is the damned SUSPEND with the fglrx proprietary driver! its so annoying!

when i try to run xorg.conf with VESA it says VESA SCREENS FOUND, BUT NO USABLE MODES.

what does that mean?

---

### Post by helliewm on 2007-09-02
I too have a Dell Inspiron 9400 with an ATIX1300 Graphics Card. Firsty forget Feisty downlaod and install Drapper in safe graphics mode. When you put in the Live CD you will the option. Its the second one down on the list.

Then follow these instructions I have just posted.

"See this thread I think its the ATI graphics card.

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I have an ATI X1300 graphics card. What I did was installed Drapper and then upgraded to Edgy. This ensured I had working internet connection. I then followed the instructions in the above THREAD [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) to install the fglxr ATI graphics drivers.

 I then upgraded to Feisty from Edgy after following the instructions to install the fglxr ATI drivers in the above thread"

Yes time consuming but quite simple and easy. I have Open GL and wobbly windows and etc and everything works.

Helen

---

### Post by di98mase on 2007-09-02
Just to be sure, will installing Drapper automatically install/create a "Dual Boot", i.e. I will be able to chose at boot if I want to run Vista or Drapper?

/di98

---

### Post by Sef on 2007-09-02
> Just to be sure, will installing Drapper automatically install/create a "Dual Boot", i.e. I will be able to chose at boot if I want to run Vista or Drapper?


No.  You have to manually partition the hard drive.

Install [alternate cd]("http://users.bigpond.net.au/hermanzone/")

Install [Live cd]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by MozartlovesUbun2 on 2007-09-02
> **di98mase said:**
> Just to be sure, will installing Drapper automatically install/create a "Dual Boot", i.e. I will be able to chose at boot if I want to run Vista or Drapper?

/di98

hi ya i had the same problems (see my PC specs below), one thing is don't loose your cool, just read up on the internet, there's lots of help for Ubuntu available, the story with this problem is some that everything worked fine on the Feisty pre-release tribes /alpha/beta versions, somehow when it came to the final release they somehow forget/missed to include the proper drivers (or what ever is needed), so that's how it happened.
So a tribe release of feisty should work, but we don't want to install tribe version :)

ok the best way i guess, or at least the way I did it, I downloaded the alternative install CD of Feisty, and read up on google how to install it, then it just updates and gets the right drivers for your ATi card.

I think I used the script from [http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/)

and that took care of all the stuff, got CompizFusion running too

it also installs Automatix, but you can remove that (Ubuntu forum people advise to install the plugins manually and not to use Automatix as it may cause problems when upgrading, like upgrading Feisty to Gutsy)

ok good luck, and don't go back to Vista, believe me have some patience and read up, it's well worth it.

If you wanna dual or triple boot make sure you have windows installed before adding ubuntu, then manually install  Feisty with the alternative CD,  or just go full Feisty all the way like me, if you need windows stuff there's Cedega for games, VMWare for full virtualised windows, or CrossOver if you wanna run Photoshop, Office apps, etc

---

### Post by Papa-san on 2007-09-02
I have an older Dell laptop and ran into a lot of problems when I switched to Ubuntu from winxp. I had never used any Linux. The experience was very frustrating. The reason I was so frustrated was that I was used to the way windows can usually be popped into almost any system, and a short time later, can be used normally. That is why it costs so much money. 

Ubuntu, like any *nix distro is going to require a change in thinking. The best thing you can do here in these forums is search... search... search! Then post. (I know, if the lingo isn't something you are used to, you miss more than not in searches.) Someone suggested Dapper Drake. I would highly recommend it. I had trouble with the previous and following versions, and most of those problems were Dell specific. Keep searching, and don't quit trying! Someday you will be able to cleanse the evil Gates monster from your box, and will be free! Theres nothing like running 100% linux! LOL 

I know, not much tech help, but I'm a reasonably effective cheerleader!

---

### Post by di98mase on 2007-09-02
Hi everybody,

Ok you have convinced me, I will read more and try again.
> then manually install Feisty with the alternative CD, or just go full Feisty all the way like me
What is the alternative CD and what is the installation CD? 
Have I understood this correctly, I have downloaded a version of Feisty that lacks the packages I need to get my graphics/display up and running. Since I boot from the CD I probably dont have any network connection and thus can not download the needed packages. As a result of this I have to get a "working" distribution for my laptop like the Dapper Drake. When I have the Dapper version on a CD I can run the OS from the CD and chose to install it or not. When the Dapper is installed I can download new packages from repositories recomended for my HW and tailor my OS as I want. Also I can chose to update to Feisty if I want to but then I must keep the packages for my graphics/display driver....

Is this conclusion correct?

---

### Post by Papa-san on 2007-09-02
Yes, that is a pretty accurate explanation. The fiesty had some issues as it went from testing to 'done', and those are likely what is causing you to pull your hair out. Sef in post #9 has links to the two different images. The alternate CD allows you some different options, so don't be afraid to keep asking for help! I promise that those guys who know what they are doing have a lot of patience... You should see some of the threads I had going... I even had some people telling me that I prolly wasn't up to the task... lol

I would honestly suggest just going with the Dapper until you are more comfortable with Ubuntu. At this point, it seems to be quite stable and inclusive of thingies we need to make our Dell's run!

---

