---
title: "Wallpaper \ Background changing with Unity Ubuntu 11.10"
date: 2011-10-22
forum: Art &amp; Design
---

### Post by drpain on 2011-10-22
Hey All,

Since the wallpaper changer I had didn't want to work any more since upgrading to 11.10 I decided to create a Python script to alter the backgrounds-1.xml file located in the /usr/share/backgrounds/contest folder. 

This is where they created the background resource file which tells the system which background to use when. What I did was create the Python script to ask you for the folder where you store your wallpapers, the frequency with which you want them to change and the time-out between wallpapers. 

I hope some of you find this helpful. You will need Python installed on the system. 

I tested it with loads 900+ images and it worked fine, images will be repeated from start to end and shuffled every time it's run. 

Kind Regards,

Rudi

---

### Post by Rodney9 on 2011-10-22
In Xubuntu 11.10 I have tried desktop nova plus wallch, but neither work, they run but the wallpaper does not change.

I tried your script, thank you, but still the wallpaper does not change.

Any clues ?

---

### Post by drpain on 2011-10-23
Hey Rodney, 

It might be simple, I hope. 

You can do the following things to find where the problem lies. Firstly something I forgot to mention is that you have to select the contest background set for it to work. 

You can do this by **Right Clicking **on the **Desktop **and clicking **Change Desktop Background**. Then you need to select the **Contest** as your desktop background.

You can check the screen-shot below, I hope it helps:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205218&stc=1&d=1319361908[/IMG]


If you still have no joy, please check the background file to see if it was amended with your backgrounds. You can do this by running the following command:

sudo gedit /usr/share/backgrounds/contest/background-1.xml

Here's my file as an example:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205219&stc=1&d=1319361908[/IMG]

Please let me know if you are able to get it to work. I might need to add some more error control.

---

### Post by mizzou_tiger on 2011-10-23
Thanks drpain!

I've been looking for something like this, worked great for me!

---

### Post by Angelus-Michael on 2011-10-24
[COLOR=RoyalBlue]***Thanks drpain ***[/COLOR]

---

### Post by drpain on 2011-10-24
I did download Xubuntu and loaded it on my Virtual PC, but it appears that they use a different desktop / appearance manager. 

This is sadly a hack for Ubuntu 11.10 specifically as the previous method didn't work.

Glad to hear some of you have been able to use it, means I didn't waste time making it!!

:popcorn:

---

### Post by lazysalamander on 2011-10-30
Thanks much, works well here.

---

### Post by drpain on 2011-11-01
Great to hear you guys are using it and it's working!

---

### Post by Hulmemanitarian on 2011-11-01
Still having trouble with it, but then I am an total ubuntu noob! :???:

---

### Post by drpain on 2011-11-01
> **Hulmemanitarian said:**
> Still having trouble with it, but then I am an total ubuntu noob! :???:

It does require some Linux / Ubuntu know-how. Lets maybe do a checklist:


1. ) Is Python Installed (Yes / No) ?

You can install it using the following command in your terminal:

sudo apt-get install python

Or you can install Python in your Ubuntu Software Center


2. ) Do you know what the absolute path of your wallpaper folder is (Yes / No)?

For example if my username is rudi and my wallpapers are in my home folder then it would be /home/rudi/wallpapers I hope this makes sense to you.

---

### Post by globalmac on 2011-11-02
Thank you drpain

---

### Post by Pynalysis on 2011-11-03
> **drpain said:**
> It does require some Linux / Ubuntu know-how. Lets maybe do a checklist:


1. ) Is Python Installed (Yes / No) ?

You can install it using the following command in your terminal:

sudo apt-get install python

Or you can install Python in your Ubuntu Software Center


2. ) Do you know what the absolute path of your wallpaper folder is (Yes / No)?

For example if my username is rudi and my wallpapers are in my home folder then it would be /home/rudi/wallpapers I hope this makes sense to you.

Cool script!!! 

Wanted to share my modification to set the default path to /home/username/Pictures folder for all interested  

# Import socket as well
import socket

# Determine hostname/username on machine
hostName = socket.gethostname()

# Set /home/user/Pictures as default path
defaultPath = "/home/%s/Pictures" % hostName

# Set Path
path = raw_input("Enter the path of the directory that contains your Wallpapers\neg. /home/%s/Pictures: " % hostName)

---

### Post by drpain on 2011-11-03
> **Pynalysis said:**
> Cool script!!! 

Wanted to share my modification to set the default path to /home/username/Pictures folder for all interested  

# Import socket as well
import socket

# Determine hostname/username on machine
hostName = socket.gethostname()

# Set /home/user/Pictures as default path
defaultPath = "/home/%s/Pictures" % hostName

# Set Path
path = raw_input("Enter the path of the directory that contains your Wallpapers\neg. /home/%s/Pictures: " % hostName)

Awesome! I am just glad so many of you used it, I previously posted a shell script which ran every five minutes but I don't think anyone used it. Nice variation there, shot for sharing!

---

### Post by jony121 on 2011-11-12
Don't wish to slag the Ubuntu team off but this seems like a very basic feature which I expected to see in 11.10 and was very disappointed not to find. I thought I was going to have to mock up something shoddy but this python script is very well done and has made me a happy penguin. 8>
Thanks drpain! <3

---

### Post by drpain on 2011-11-12
Same here, the Ubuntu team is awesome and I am sure they have bigger fish to fry then something like this. I am just glad you were able to use the hack. 

Who knows if they will have future releases using this desktop manager, it would server us well if someone can creates a GUI version of this (I am a very basic programmer at best and PHP is my forte).

---

### Post by mojo636 on 2011-11-17
Thanks drpain, finally i found something that works!! script worked like a charm.

---

### Post by Dr3wbi3 on 2011-12-15
So You can use this script or crebs to make xml files ... I had an issue where their were files that wouldnt work so i thought it was the script but after trying to compile the xml with Crebs i got some errors about some files that couldnt be included. 
So I removed those files and things started working ok.
 so now i want to have multiple slideshows to switch from (this is working for some but not all dunno why)

go to /usr/share and now open gnome-background-properties as root and then edit the ubuntu-wallpapers.xml
with the following code to point to each new slide show you make.

<wallpaper deleted="false">
    <name>**YOUR NAME HERE**</name>
    <filename>**/usr/share/backgrounds/Contest/Contest.xml**</filename>
    <options>Scale</options>
  </wallpaper>

(replace the bold fields with your names and paths)
this way you can also point to the crebs directory as well
then save and exit the file and logout or restart

---

### Post by ebichuhamster on 2011-12-22
Im having trouble with this script.

I installed it, it worked, it did what i wanted.

Then i had to reboot and suddenly i cant access anything in my desktop and i am very new to linux/ubuntu so i don't know the necessary shortcuts or anything.

I appreciate any help!

---

### Post by ebichuhamster on 2011-12-23
I'm pretty sure Unity somehow crashed and it is not getting up.  

I tried unity --reset but it just responded something like "no window display enabled".

Does anyone know what went wrong?? >_< I think i'm looking in all the wrong places...

---

### Post by surya16 on 2011-12-26
thank you

---

### Post by tusjr on 2012-01-06
Does anybody know if it is possible to add several changing backgrounds in Ubuntu 11.10? I've tried to add more background-1.xml-files according to the directory layout as given for the Contest wallpaper, but it does not get recognized in the appearance window, aka the window to set the wallpaper. It looks like this was possible in 11.04 where you could add another xml-file to the selection, but this possibility seems to have been removed in 11.10.

---

### Post by drpain on 2012-01-06
> **tusjr said:**
> Does anybody know if it is possible to add several changing backgrounds in Ubuntu 11.10? I've tried to add more background-1.xml-files according to the directory layout as given for the Contest wallpaper, but it does not get recognized in the appearance window, aka the window to set the wallpaper. It looks like this was possible in 11.04 where you could add another xml-file to the selection, but this possibility seems to have been removed in 11.10.

I also tried that hey. But the one file should be fine as long as you have all your wallpapers in one folder. All the other wallpaper changers no longer work on 11.10 so at least this way you can change them.

---

### Post by livelite on 2012-02-06
Thanks for the wonderful script!  Yeah I thought Ubuntu already had this feature, but this script works wonderfully.  I'm sure Ubuntu will have it native soon.

---

### Post by drpain on 2012-02-06
> **livelite said:**
> Thanks for the wonderful script!  Yeah I thought Ubuntu already had this feature, but this script works wonderfully.  I'm sure Ubuntu will have it native soon.

You are welcome, just doing my bit to help out. I do really hope they support it, because it something small but nice to have.

---

### Post by eklem on 2012-02-10
drpain, Maybe you want to join me, [making a seasonal desktop background changer]("http://brainstorm.ubuntu.com/idea/29179/"), and try to package it as a .deb-file?

---

### Post by drpain on 2012-02-13
> **eklem said:**
> drpain, Maybe you want to join me, [making a seasonal desktop background changer]("http://brainstorm.ubuntu.com/idea/29179/"), and try to package it as a .deb-file?
I would love to, but unfortunately, I am quite busy these days with work and so on. If my script helps at all please feel free to use it at your own discretion.

---

### Post by eklem on 2012-02-14
> **drpain said:**
> I would love to, but unfortunately, I am quite busy these days with work and so on. If my script helps at all please feel free to use it at your own discretion.

Ah, cool: I'll start with your script and see how far I get (I'm not a programmer, but can code some). And I'll keep you updated on the progress.

---

### Post by zima3000 on 2012-02-25
Thanks for the script! Worked like a charm

---

### Post by Xeletron on 2012-03-02
wallch does this task verry well also. look in the repo's voor wallch wallpaper changer.  [http://shuffleos.com/2231/wallch-change-wallpapers-automatically-ubuntu/](http://shuffleos.com/2231/wallch-change-wallpapers-automatically-ubuntu/)

---

### Post by Xero Xenith on 2012-03-05
> **Xeletron said:**
> wallch does this task verry well also. look in the repo's voor wallch wallpaper changer.  [http://shuffleos.com/2231/wallch-change-wallpapers-automatically-ubuntu/](http://shuffleos.com/2231/wallch-change-wallpapers-automatically-ubuntu/)

Works nicely! Took some playing to get it to change at first, but now it works well. (I had to change the wallpaper in the normal Settings option to "Contest" before it worked.)

---

### Post by smuthavarapu on 2012-03-13
This is working cool. thank you for sharing.  I hope Unity fix the issue with Single instance

---

### Post by thietkelogo on 2012-03-20
I am looking for something like this, please to see more

---

### Post by cooler95 on 2012-06-23
Great I tried it in ubuntu 12.04 just had to chance the name of the output file to precise and worked

---

### Post by drpain on 2012-07-01
Awesome thanks, I am busy downloading 12.04 now.

---

### Post by xfctr on 2012-08-19
You can also try Variety Wallpaper Changer - a new application that I recently created. Is supports changing wallpapers from local sources, fetching from various online sources, applying effects on the fly and has many more nice features. You'll need Ubuntu 12.04 or newer for it, or a new version of Mint.
Screenshots, video demo and installation instructions are all here: [https://launchpad.net/variety](https://launchpad.net/variety)

---

### Post by Rodney9 on 2012-08-22
> **xfctr said:**
> You can also try Variety Wallpaper Changer - a new application that I recently created. Is supports changing wallpapers from local sources, fetching from various online sources, applying effects on the fly and has many more nice features. You'll need Ubuntu 12.04 or newer for it, or a new version of Mint.
Screenshots, video demo and installation instructions are all here: [https://launchpad.net/variety](https://launchpad.net/variety)


Works well in Xubuntu 12.04, thank you.

Rodney

---

### Post by jooiiee on 2012-12-06
To make it work on 12.04 (probably 12.10 to) you need to run the following commands.   

```

sudo mv /usr/share/backgrounds/contest/precise.xml /usr/share/backgrounds/contest/precise.xml.backup 
# 
sudo mv /usr/share/backgrounds/contest/background-1.xml /usr/share/backgrounds/contest/precise.xml 
```Then select the community wallpapers. 
Works great for me after changing the filename! :D

---

### Post by meggie on 2013-04-09
If anyone was still watching this forum for Ubuntu 12.10 wallpaper changing, you don't need to have the exact name and location of quantal.xml.
Just make your xml file wherever you want (e.g. animals.xml).
Go to /usr/share/gnome-background-properties and make a copy e.g. of the ubuntu xml. Leave as many wallpaper records as you need, just fill the <name> and full path to <filename>.

cd /usr/share/gnome-background-properties
sudo cp ubuntu-wallpapers.xml my-wallpapers.xml
sudo vim my-wallpapers.xml   ...
...
<wallpaper>
<name>Animals</name>
<filename>/home/meggie/animals.xml</filename>
...
Enjoy! :KS

---

