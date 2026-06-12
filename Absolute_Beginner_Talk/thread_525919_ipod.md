---
title: "ipod"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-08-14
I plugged my grandsons new nano into ubuntu 7.04 it was recognized and rhythm box opened as well. 

I dragged and dropped music files into the nano. I know they are there, because I double checked with our windows machine and it shows them to be there. I just can not find them on the nano pod. Where are they located?

---

### Post by felicity on 2007-08-14
I could be wrong, but I believe you aren't seeing the songs on the nano because you need to update it's song database, which rhythmbox doesn't do as far as I know.

I personally use [Floola]("http://www.floola.com/modules/wiwimod/") but [Gtkpod]("http://www.gtkpod.org/about.html") is pretty popular too and in the repositories.

---

### Post by rosswmcgee on 2007-08-14
Well I just dragged them from the album folder to the Nano, what should I have done?

---

### Post by felicity on 2007-08-15
Perhaps try using an ipod management program like floola or gtkpod.

---

### Post by R0B071CxN1NJ4 on 2007-08-15
> **rosswmcgee said:**
> Well I just dragged them from the album folder to the Nano, what should I have done?
I use a program called Banshee. it needs to be built from source if i am correct. but it works great and it imitates itunes extremely well. You should try that.

---

### Post by rosswmcgee on 2007-08-15
I will try it if it works fine if not I will try the gtkpod. The gtkpod looks  a wee daunting.

---

### Post by Ripfox on 2007-08-15
Banshee: [http://www.getdeb.net/app.php?name=Banshee](http://www.getdeb.net/app.php?name=Banshee)

Easy install.

---

### Post by rosswmcgee on 2007-08-15
OK I imported the songs into Banshee. I used windows to activate the Ipod it is working, how ion the world do I get the songs from banshee or rhythm box into the ipod? I drag them there banshee shows that they are there, but when I disconnect the ipod and turn it on the recordings are not found. Please advise. It  is beginning to look like my grandsons birthday present is a night mare.:(

---

### Post by Hobo Joe on 2007-08-15
I know you don't want to do this, but you need to install another program.

Amarok. It's the best music player out there in my opinion, and it has fabulous support for iPods. To install you just type:
```

sudo aptitude install amarok

```
Then once you have it installed, go to Settings > configure Amarok. Then click on media devices, and press add new, then change the type to Apple iPod device. Then just move whatever songs you want!

---

### Post by rosswmcgee on 2007-08-15
OK will try it not a problem. Thanks Ross

---

### Post by laidback on 2007-08-15
Use Amarok, it works fine for me.

---

### Post by rosswmcgee on 2007-08-15
I have now tried Amarok, Rhythmbox, and Banshee, all detect the music. When I drag a tune as I just did from Amarok to the Nanopod it shows it to be in the nanopod, the nano shows it on the computer to be there as well, but when I disconnect the nano and turn it on there is not song?

What gives here?:(

---

### Post by Hobo Joe on 2007-08-15
Try resetting the nano, hold down center button and menu button for 5 seconds.

---

### Post by R0B071CxN1NJ4 on 2007-08-15
> **Hobo Joe said:**
> I know you don't want to do this, but you need to install another program.

Amarok. It's the best music player out there in my opinion, and it has fabulous support for iPods. To install you just type:
```

sudo aptitude install amarok

```
Then once you have it installed, go to Settings > configure Amarok. Then click on media devices, and press add new, then change the type to Apple iPod device. Then just move whatever songs you want!
Argh i cant believe i forgot about amarok how f***ing stupid of me pardon me french

---

### Post by R0B071CxN1NJ4 on 2007-08-15
> **rosswmcgee said:**
> I have now tried Amarok, Rhythmbox, and Banshee, all detect the music. When I drag a tune as I just did from Amarok to the Nanopod it shows it to be in the nanopod, the nano shows it on the computer to be there as well, but when I disconnect the nano and turn it on there is not song?

What gives here?:(
I have a nano but i havent yet synced it with linux. (i have dual boot so i didnt even think about it) and ill try amarok and get back to you

EDIT: Alright im back and synced up. heres what i did

install amarok as you have done:

```
# sudo apt-get install amarok
```

Setup the ipod as amarok told me as youve done

then when i went to sync the file i had to delete the files that were on there then drag the files and press transfer because it did the same thing to me as it did to you

---

### Post by rosswmcgee on 2007-08-15
OK! when I drag the song to the ipod icon is there a special folder it needs to be in? Because just dragging the song to the ipod although it is there, when I disconnect the ipod
there is still no song to be seen.

---

### Post by Ripfox on 2007-08-15
I have had no luck with ipods on Ubuntu apart from Floola. It works like itunes pretty much.

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

---

### Post by Hobo Joe on 2007-08-15
> **rosswmcgee said:**
> OK! when I drag the song to the ipod icon is there a special folder it needs to be in? Because just dragging the song to the ipod although it is there, when I disconnect the ipod
there is still no song to be seen.

AHHHH, now I know the problem. First, make sure that the iPod is setup as 'Apple iPod device', and then press 'connect.'

While you are in Amarok,(NOT the file browser)Select all the music you want, and then right-click, and press 'transfer to device', the click on the device tab on the left, and press the transfer button at the top.

I hope that helps. :)

---

### Post by rosswmcgee on 2007-08-15
I give up and am returning the Nano. I would rather my grandson read A dangerous book for boys.

---

### Post by Hobo Joe on 2007-08-15
> **rosswmcgee said:**
> I give up and am returning the Nano. I would rather my grandson read A dangerous book for boys.


NOOOOO don't give up!

---

### Post by Ripfox on 2007-08-16
Weird response...is this guy really a grandfather lol (my grandpa is 98, he never gives up) :guitar:

---

### Post by rosswmcgee on 2007-08-16
Well actually I haven't. Thanks you made me laugh!

---

### Post by Hobo Joe on 2007-08-16
First question: Is your music in the Amarok library?

Second, if it is, how are you transfering it.

Third, is your nano set as an Apple iPod device?

---

### Post by Arthur Archnix on 2007-08-16
You may have messed up the filesystem on your ipod at this point. I'd use itunes to restore it to factory defaults, then boot up and follow the instructions above for how to transfer files using amarok.

---

### Post by rosswmcgee on 2007-08-16
Very helpful. It seems Amarok recogizes the ipod nano blue, connect is greyed out, so I pushed transfer and all the songs got red circles with x's in it. However after all is done still no songs on the nano pod. Weird.

---

### Post by Hobo Joe on 2007-08-16
Ok, I think I know the problem now.

Click on the little double arrow next to transfer, and then click configure.

In the box there is a list of formats that will transfer, by default it is only mp3, you need to add acc, mp4, m4a, possibly a few others.

---

### Post by Arthur Archnix on 2007-08-16
Can you maybe bring us all up to speed, and lay out exactly what you've done so far?
1. Installed Amarok, obviously.
2. Have you reset the ipod to factory defaults?
3. Have you told Amarok to manage the ipod?
4. You said "connect" is grayed out. That could mean it's already connected, or that it doesn't think anything is connected. Is there an ipod icon on your desktop? And 3. above?
5. Start by trying to transfer just one file. Make sure it's an .mp3. Right-click and send to device. Then, there's probably a button that says transfer. Someone above gave more detailed instructions.

EDIT: Sounds like poster above has a better idea of what's going on. Try that first. :)

---

### Post by rosswmcgee on 2007-08-16
more: Amarok says nine tracks not playable on media device, at the bottom, i see that but do not know why. This is music from a CD transfered to Amarok from the sound juicer.

I tried it with just one track and the same thing happened.

---

### Post by Arthur Archnix on 2007-08-16
What's the file extension of the music you ripped in sound juicer?

If it's .ogg it will never work and you'll have to re-rip the music in another format. AAC or MP3

---

### Post by rosswmcgee on 2007-08-16
So it was an ogg file ext. So would you recomend I get rid of sound juicer and replace it with 
some thing else?

---

### Post by Arthur Archnix on 2007-08-16
Not at all. From all I've read soundjuicer is one of the best ripping programs out there. You'll just need to tell it to rip the music as an mp3 or aac in order for it to be playable on the nano. I'm afraid I don't know exactly how to do it, only that it is very easy to accomplish. Perhaps someone else will tell you how if you don't figure it out yourself by then.

EDIT: preferences, output format, change to mp3

---

### Post by rosswmcgee on 2007-08-16
So it was an ogg file ext. So would you recomend I get rid of sound juicer and replace it with
some thing else?

---

### Post by rosswmcgee on 2007-08-16
Ok I'll give it a try. I am going to stay at this till I get the job done some how with the help of the Ubuntu folks, and thank you.

---

### Post by rosswmcgee on 2007-08-16
I do not see how sound juicer lets you do that.

---

### Post by Arthur Archnix on 2007-08-16
Edit, preferences, look down near the bottom where it says formats.

---

### Post by t2000kw on 2007-08-16
Banshee can be installed with Synaptics without the need to compile it.

---

### Post by rosswmcgee on 2007-08-16
It gives four options:

 Ogg which we do not want
flac audio
voice wav audio
Voice lossy 

Which do I need? to convert the cd to an acceptable ipod file ext.

---

### Post by Arthur Archnix on 2007-08-16
Oh that's interesting. You must not have mp3 support installed yet. Try closing down soundjuicer. Then do this:
```
sudo apt-get install ubuntu-restricted-extras
```
You'll need to do this in a terminal and leave it open, so that you can say yes to a bunch of licenses. After that's done, restart soundjuicer and go back to where you were, we're hoping that now we'll find mp3 as an option as well.

---

### Post by t2000kw on 2007-08-16
Just checked, Ubuntu-restricted-extras is available with Synaptics also, if you like the GUI approach. Automatix also has it, but it has some potential problems. Use it at your own risk!

---

### Post by rosswmcgee on 2007-08-16
Great I will give it a try. I did move an mp3 from amaroks selections to the ipod and it worked perfectly thanks you so much for your patience.

---

### Post by Arthur Archnix on 2007-08-16
According to the soundjuicer forums, this is the only package you need to rip cd's into mp3 format:
```
sudo apt-get install gstreamer-0.8-lame package
```
I'd still install the restricted extras above though, it enables a lot of popular content online and such. And it may also install the gstreamer plugin. If not, just run that one command and you should be good to rip away.

---

### Post by Lord Illidan on 2007-08-16
> **rosswmcgee said:**
> Great I will give it a try. I did move an mp3 from amaroks selections to the ipod and it worked perfectly thanks you so much for your patience.

Cheers!

---

### Post by rosswmcgee on 2007-08-16
Now Igoofed things up,I thought terinal was fnished here is the problem

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I do t know what t do.

---

### Post by Arthur Archnix on 2007-08-16
Let's just try doing what it says.
```
sudo dpkg --configure -a
```
Afterwards, do 
```
sudo apt-get update
sudo apt-get upgrade
```
then, just to be sure all is well, do the ubuntu restricted drivers again. If it's already installed fine it will just say "nothing to see here folks", or something. Otherwise it will finish up with its installation.

---

### Post by rosswmcgee on 2007-08-16
Ok all is well I now have the option of mp3 audio, so do I have to burn a new cd or simply extract with the new preference? You sure know your stuff.

---

### Post by Arthur Archnix on 2007-08-16
Not too sure what you mean by burn a cd, but I don't think so. Just extract that juice with the mp3 settings, and it sounds like you've already got the nano working with amarok. You've got a lucky grandkid there. My grandpa would've told me to learn to sing if he had this much trouble getting my walkman going. ;)

---

### Post by rosswmcgee on 2007-08-16
Well all is working job well done folks I will stick with Amarok.

---

### Post by t2000kw on 2007-08-16
I am thinking of buying an MP3 player. I'm not overly impressed with the Ipod but I'm not knocking it, either. I just want more value for the money, that's all. Ipod is a great, high quality product. 

Can anyone recomend an MP3 player that works well with Linux and is very easy to navigate with the supplied controls, and hopefully is upgradable?

---

### Post by Ripfox on 2007-08-16
> **Arthur Archnix said:**
> My grandpa would've told me to learn to sing if he had this much trouble getting my walkman going. ;)

Now THAT'S funny. :)

---

### Post by AlbinoButt on 2007-08-17
I'm having the same exact problem with my nano. It shows up as an iPod device, I see it in banshee, exaile, and rhythmbox. I can add files to the nano fine using all three programs and I can even see the mp3 files on my iPod while browsing through the filesystem (in Nautilus). But when I use my iPod, it shows absolutely no songs.

(I definitely don't want to use amaroK.)


I've done everything including restoring it and resetting it as indicated in previous posts and nothing has fixed the problem.

---

### Post by Ripfox on 2007-08-17
I still say Floola.

---

### Post by AlbinoButt on 2007-08-17
I'd like to find out how to fix this problem instead of just giving up and switching to another piece of software.

Maybe this has to do with the iPod's firmware/software version? (Mine is 1.3.1)

---

### Post by Arthur Archnix on 2007-08-17
Well Albino, I'm not familiar with anything but Amarok. So if you want to use that for now I may be able to help you troubleshoot. You can always uninstall it after you get your nano working and use another piece of software knowing that there are no underlying problems other than a specific piece of software.

---

### Post by AlbinoButt on 2007-08-17
I don't have any of the KDE/QT libraries installed right now, nor do I plan to use any of those kind of apps. I've already tried 3(!) different pieces of software and none of them work. 

Jumping to Floola, then Amarok then insert app here, just for troubleshooting purposes, doesn't seem reasonable to me. There should be *some way* to get my nano working on either Banshee, Exaile, or Rhythmbox.

---

### Post by Ripfox on 2007-08-17
Yea, but Floola works better than those apps:popcorn:

---

### Post by Arthur Archnix on 2007-08-18
> **AlbinoButt said:**
> I Jumping to Floola, then Amarok then insert app here, just for troubleshooting purposes, doesn't seem reasonable to me.

Ok. You're right in that you can probably solve this without doing that, and I hope you find your answer.

---

### Post by rosswmcgee on 2007-10-21
sudo apt-get install ubuntu-restricted-extras
[sudo] password for mickey:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mickey@mickey-desktop:~$ 
Hi back again trying to fix gutsy sound jucier so that it reads mpg filles likewe did in 7.04 but this is what I get in terminal.

---

