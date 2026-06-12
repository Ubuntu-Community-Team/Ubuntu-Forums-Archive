---
title: "Which Version of linux is right for me?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by todd_freeride on 2007-08-31
Hello, I've never really used linux much before, I had an old system that no linux would run on for no reason at all. but I found a newer system (Dell Dimension 4300, 1.7 ghz P4, 250GB hard drive, 512MB of DDR RAM) I picked it up with an illeagal copy of XP pro on it. I had installed sabayon...this was because I heard it already came with beryl installed and it would save me a lot of work. but I somewhat gave up after it wouldn't recognize the wireless card. Dell was kind enough to send me a version of XP Home that came with my system. when I re-installed windows it took away my dual boot. now the sabayon disc wont load. 

So, frustrated with asking for help on these forums and getting nasty responses on how dare I ask for help with sabayon :( Not to mention all the skins and items coming out for linux are designed to run ubuntu, not some other version.

So...I need ubuntu. but now theres two versions... I've fallen in love with the LOOK of Ubuntu Studio. It also comes with programs I would actually use. especially with the audio and video software. But this is a text based installer, can I still dual boot my system with Studio? I will not ditch windows for linux entirely, so I DO need to dual boot. the Ubuntu Studio is not a live DVD either : \ so no try it before you "buy" it. 

So what I'm wondering, is based on my PC's specs, what I need to use on linux but also my limited knowledge of UNIX and needing to dual boot...which version should I get? Ubuntu or Ubuntu Studio?

--> Vid of Sudio if you havent seen it yet. [http://youtube.com/watch?v=YAz29JMyCRs](http://youtube.com/watch?v=YAz29JMyCRs) (warning, loud annoying NSFW music)

Thank you so much for your time.

---

### Post by wolfen69 on 2007-08-31
either distro will see your xp partition and dual boot just fine.

---

### Post by diatribe on 2007-08-31
[http://www.howtoforge.com/ubuntustudio_7.04](http://www.howtoforge.com/ubuntustudio_7.04)

---

### Post by raijinsetsu on 2007-08-31
I'm sorry some people got angry about you asking or help with sayabon on a Ubuntu forum, but... it is a Ubuntu forum.
Secondly, you can still probably restore your old dual-boot. Just boot up with almost any linux install CD (prefer Gentoo, as it has the most system tools available during install), and install grub. Google up a linux dual boot howto. :)

---

### Post by Paul133 on 2007-08-31
Who blew you off because you needed help with Sabayon? I mean, if you have Sabayon, you'll get better help on their forums, but most Ubuntu forum members are not known to be rude to newbies.

---

### Post by Majorix on 2007-08-31
I don't like Sabayon and the way they treat their potential users. I even had a thread about this in the community cafe here.

Anyways, if you REALLY need Beryl, you could wait for Ubuntu 7.10, which will eventually come with Compiz Fusion in October. Or if you have to found a computer system right now you could try the alpha version of it. Warning though, it can and will contain bugs here and there.

I have never tried Ubuntu Studio though I believe all programs it uses can be installed on a standard Ubuntu install. sudo apt-get install is your friend.

If you need any help about it, feel free to create another topic about it here.

---

### Post by afonic on 2007-08-31
If you are new, get the Ubuntu 7.04 official.

Can't get any better. :)

---

### Post by por100pre1 on 2007-08-31
Get a Regular Ubuntu 7.04 LIveCD, install Ubuntu and reboot. When finished copy/paste and ENTER each one of these lines one by one in a program called **Terminal** (It should be in **Applications> Accessories> Terminal**:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This transforms Ubuntu Feisty  into Ubuntu Studio with all its software.

Hope this helps.
:guitar:

---

### Post by todd_freeride on 2007-08-31
> **Paul133 said:**
> Who blew you off because you needed help with Sabayon? I mean, if you have Sabayon, you'll get better help on their forums, but most Ubuntu forum members are not known to be rude to newbies.

I got an e-mail and a PM from two different members. one of which referred to me as "we dont want your kind here..." I laughed pretty hard, but still...it was odd. Then the e-mail I got was like a hate e-mail? Telling me that I need to go back to mac os 9. I'm sure thats probably the same guy just trying to mess with me. but oh well.

I didnt know that there was a sabayon forum, I had just typed in "linux help" into google. found ubuntu forums and it seemed like there were lots of knowledgeable people here.

---

### Post by por100pre1 on 2007-08-31
> **todd_freeride said:**
> I got an e-mail and a PM from two different members. one of which referred to me as "we dont want your kind here..." I laughed pretty hard, but still...it was odd. Then the e-mail I got was like a hate e-mail? Telling me that I need to go back to mac os 9. I'm sure thats probably the same guy just trying to mess with me. but oh well.

I didnt know that there was a sabayon forum, I had just typed in "linux help" into google. found ubuntu forums and it seemed like there were lots of knowledgeable people here.

Did you get that PM in these forums? If so please report it immediately!!! I'm sure that kind of behavior is not tolerated here.

---

### Post by meborc on 2007-08-31
> **todd_freeride said:**
> I got an e-mail and a PM from two different members. one of which referred to me as "we dont want your kind here..." I laughed pretty hard, but still...it was odd. Then the e-mail I got was like a hate e-mail? Telling me that I need to go back to mac os 9. I'm sure thats probably the same guy just trying to mess with me. but oh well.

I didnt know that there was a sabayon forum, I had just typed in "linux help" into google. found ubuntu forums and it seemed like there were lots of knowledgeable people here.
sorry to hear that. linux is all about freedom of choosing the best for YOUR system... i hope you don't get discouraged because of few people with too little love in their lives :D

i suggest you try out few of the most popular distros (use live cd's so you don't need to install anything)... you can get more info on different distros @ distrowatch

---

### Post by por100pre1 on 2007-08-31
Can you please post that PM here? That shouldn't be ignored.

---

### Post by svalding on 2007-08-31
In your search you will probably find that Ubuntu is one of the easiest distros to learn and use. 

Synaptic is a wonderful tool to easily install any packages you may need, and the applications manager allows you to install pretty much any linux program you could possibly need. 

As for using Ubuntu studio, if you are going to run it on the current system you described, upgrade the ram. I have run Studio, and it is rather taxing on your system when you start doing a lot of video/audio editing. The tools it has included are very nice though. 

Follow the previous posters advice and install the studio packages using the Terminal commands he has pasted. 

Good luck with your learning, and the community here is always ready to help with any issue you may have.

---

### Post by Brightbelt on 2007-08-31
Hi, Welcome....Don't be put off that Ubuntu Studio is a text installer. It is fairly easy. If I can do it, anyone can. :)

Also, I like to inform folks of a distro which I consider to be an Ubuntu alternative, just in case Ubuntu doesn't work for you. Mandriva has a very user friendly install and desktop interface. 
Admittedly, the Mandriva community is nowhere near as focused as Ubuntu's. But it is a good distro. 

Good Luck, Frank B.

---

### Post by r4ik on 2007-08-31
Someway Somehow get that PM to the forum staff if you don't want to post it here.
Welcome to Ubuntu !

:popcorn:

---

### Post by todd_freeride on 2007-08-31
hey everyone thanks for the concern over that PM. I went to look for it, but its just gone. So I'm guessing that it was either in a different computer forum I use (highly ...highly doubt it) But I'm guessing the guy was banned or something, because the post is non existent. 

I'll look into RAM, problem is I have 2X 256MB : \ I was opening up my system really hoping for a single 512. ohh well. sad part is, I'll pay more for RAM than I did the whole computer :p ohh well, maybe I'll find some cheap somewhere. DDR shouldent be too spendy now. (I just put 512DDR in my other system and it was like $29.99.

---

### Post by por100pre1 on 2007-08-31
> **todd_freeride said:**
> hey everyone thanks for the concern over that PM. I went to look for it, but its just gone. So I'm guessing that it was either in a different computer forum I use (highly ...highly doubt it) But I'm guessing the guy was banned or something, because the post is non existent. 

I'll look into RAM, problem is I have 2X 256MB : \ I was opening up my system really hoping for a single 512. ohh well. sad part is, I'll pay more for RAM than I did the whole computer :p ohh well, maybe I'll find some cheap somewhere. DDR shouldent be too spendy now. (I just put 512DDR in my other system and it was like $29.99.

I think 256MB is the minimum for Ubuntu 7.04. IMHO you can upgrade your memory as you said (512MB would be good for Ubuntu). In the meanwhile you can install Xubuntu, which uses less memory, and when you upgrade your memory you can then add ubuntu-desktop (the default Ubuntu GNOME installation files) to Xubuntu easily.

---

### Post by todd_freeride on 2007-08-31
> **por100pre1 said:**
> I think 256MB is the minimum for Ubuntu 7.04. IMHO you can upgrade your memory as you said (512MB would be good for Ubuntu). In the meanwhile you can install Xubuntu, which uses less memory, and when you upgrade your memory you can then add ubuntu-desktop (the default Ubuntu GNOME installation files) to Xubuntu easily.

What I meant was I have 2 - 256MB cards, so 512 total. But I wish it was a single 512 then I could get 1GB.

---

### Post by Dark Hornet on 2007-08-31
To answer your question regarding which flavor of Ubuntu is right for you....It is a personal thing---you need to decide what "look and feel" you like.  If I might give you a piece of advice...based on the specs of your computer, I would go with regular Ubuntu, as video and music programs tend to take up a lot of system resources, and I would recommend you upgrade before you start getting into some higher end video stuff.  If you are just after the "look" of Ubuntu Studio, you can always download and use the theme, and background, etc.  Have fun, and I hope this helps.

---

### Post by todd_freeride on 2007-08-31
yea, well I used to edit on 256MB using pinnacle and studio 10. I'm sure with all the beryl settings installed 512 will be the minimum. I guess I should clarify, I do a LOT of work with images, I edit videos and put them on youtube, I also like to record and modify my own music. I also used to do all this on 256MB on my windows computer so I kinda know what I'm getting into. I've never had over 1GB of RAM on a windows computer. (4GB on a G5) then 768 on this current computer. (not enough hard drive space to install ubuntu, for the price of a hard drive I could get 1GB RAM for the Dell, so : \

---

### Post by por100pre1 on 2007-08-31
> **Dark Hornet said:**
> To answer your question regarding which flavor of Ubuntu is right for you....It is a personal thing---you need to decide what "look and feel" you like.  If I might give you a piece of advice...based on the specs of your computer, I would go with regular Ubuntu, as video and music programs tend to take up a lot of system resources, and I would recommend you upgrade before you start getting into some higher end video stuff.  If you are just after the "look" of Ubuntu Studio, you can always download and use the theme, and background, etc.  Have fun, and I hope this helps.

**Todd Freeride**, I think this could be a good solution for your installation plans. If you just want the Ubuntu Studio looks do as I told you before, just replace the last line with this:

```
sudo aptitude install ubuntustudio-look
```

---

### Post by ts51 on 2007-08-31
> **todd_freeride said:**
> Hello, I've never really used linux much before, I had an old system that no linux would run on for no reason at all. but I found a newer system (Dell Dimension 4300, 1.7 ghz P4, 250GB hard drive, 512MB of DDR RAM) I picked it up with an illeagal copy of XP pro on it. I had installed sabayon...this was because I heard it already came with beryl installed and it would save me a lot of work. but I somewhat gave up after it wouldn't recognize the wireless card. Dell was kind enough to send me a version of XP Home that came with my system. when I re-installed windows it took away my dual boot. now the sabayon disc wont load. 
 
So, frustrated with asking for help on these forums and getting nasty responses on how dare I ask for help with sabayon :( Not to mention all the skins and items coming out for linux are designed to run ubuntu, not some other version.
 
So...I need ubuntu. but now theres two versions... I've fallen in love with the LOOK of Ubuntu Studio. It also comes with programs I would actually use. especially with the audio and video software. But this is a text based installer, can I still dual boot my system with Studio? I will not ditch windows for linux entirely, so I DO need to dual boot. the Ubuntu Studio is not a live DVD either : \ so no try it before you "buy" it. 
 
So what I'm wondering, is based on my PC's specs, what I need to use on linux but also my limited knowledge of UNIX and needing to dual boot...which version should I get? Ubuntu or Ubuntu Studio?
 
--> Vid of Sudio if you havent seen it yet. [http://youtube.com/watch?v=YAz29JMyCRs](http://youtube.com/watch?v=YAz29JMyCRs) (warning, loud annoying NSFW music)
 
Thank you so much for your time.
 
 
 
Just install Feisty and install UbuntuStudio's theme. I personally think it is the ugliest theme you could possibly get, but that's the glory of linux. You choose. Not one person that is named Steve or Bill.

---

### Post by todd_freeride on 2007-09-01
yea, but then I have to go and find and install everything onto normal ubuntu, it already comes on studio, isnt studio going to be a better choice for my needs then?

---

### Post by carusoswi on 2007-09-01
> **todd_freeride said:**
> yea, but then I have to go and find and install everything onto normal ubuntu, it already comes on studio, isnt studio going to be a better choice for my needs then?

I am curious.  What are the applications that come with Studio that have you so turned on to that flavor of Ubuntu?  I would love to do my audio/video editing in Ubuntu, but, have, as yet, not found a single video ap that I feel is up to the task, and, I have yet to find an audio ap that even works on my machine (perhaps that is a problem for some other thread) as none of them will fully function with my two audio cards (I have a less than adequate onboard audio card and an Audigy 2 PCI audio card in my little PCX system)

Multimedia issues more than any other problem has kept me going back to XP regularly.  FWIW, I use Sony's (formerly Sonic Foundry's) suite of audio/video applications (Vegas, Sound Forge, DVDArchitect) and Steinberg's Wavelab/Nuendo for more demanding live audio, audio editing, CD compilation, etc., not that most anything I do using Steinberg aps could not also be accomplished from the Sony Suite.

I would die to get anything near that functionality from within Ubuntu.  I also own Crossover, but it does not support those applications - I guess it has something to do with their need to call on vast libraries of dlls that probably serve more than one application and which do not get installed globally in the Codeweaver setup (each application seems to be installed with its own mini-virtual replication of a Windows setup, so applications such as those mentioned above or more recent versions of Photoshop will not load and run properly.

So, if you don't mind, please share the names of those linux applications you use for your multimedia work.

Caruso

---

### Post by todd_freeride on 2007-09-01
well, thats just the problem...I DONT use any linux apps because I dont know what I'm doing with computers so much when it comes to dual booting, so I'm waiting for a friend to come and help me with it. 

I would LIKE to use Ardour 2 to try some audio. I'm used to garage band. Inkscape and Blender for images as well as Gimp. PiTiVi, Kino, Cinepaint for video stuff, I'm used to final cut studio pro, iMovie and WMM. (but I mainly use studio 10 and final cut, wouldent expect anything near that for free)

---

### Post by todd_freeride on 2007-09-01
does anyone know where I can download ubuntu studio other than off their website? They must be on dialup or something, I downloaded regular ubuntu in about 25 minutes. so Its not my connection problem. 

I cant just wait for it to download, I'm on a WLAN T1 connection, despite being 25 feet away from the unit, my connection about every hour gets dropped for like a second, then re connects.

I cant have none of this 
[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/crap.jpg[/IMG]

---

### Post by Lucifiel on 2007-09-01
Try using this torrent instead:

[http://ubuntustudio.org/files/UbuntuStudio_7.04.torrent](http://ubuntustudio.org/files/UbuntuStudio_7.04.torrent)

---

### Post by nonewmsgs on 2007-09-01
> **por100pre1 said:**
> Get a Regular Ubuntu 7.04 LIveCD, install Ubuntu and reboot. When finished copy/paste and ENTER each one of these lines one by one in a program called **Terminal** (It should be in **Applications> Accessories> Terminal**:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This transforms Ubuntu Feisty  into Ubuntu Studio with all its software.

Hope this helps.
:guitar:

i would just do that...is something not working for you?  

also welcome here and im sorry about that rude person/rude people.  we have forums for window and other OSes in general and i have gotten help with different OSes myself independant of the program i like.

---

### Post by todd_freeride on 2007-09-01
hmm, so entering these codes will give me everything thats in studio? 

I have an ubuntu disc...my CD burner wouldent allow for anything less than 10X though when writing it. I ran it for a little bit on this system, but then it locked up.

I just dont want to hassle with downloading and installing software, not to mention configuring it.

---

