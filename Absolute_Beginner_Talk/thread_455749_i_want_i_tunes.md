---
title: "i want i tunes"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by drakebahamut on 2007-05-26
i have the new umbuntu and i want itunes. i have installed wine and i was told it would work. but when i download itunes and try to install it a window comes up and it says     Fatle error can not load picturs  or least somthing like that can sombody help me?

---

### Post by jackmc on 2007-05-26
Can I ask why you want it?

---

### Post by machoo02 on 2007-05-26
Have you checked the iTunes page over at the [Wine Application Database]("http://appdb.winehq.org/appview.php?iAppId=1347") to see if there are any special instructions for installing it?  Also, why not use one of the many native (i.e., linux) music players, such as amaroK or rhythmbox?  If you are worried about being able to use you ipod, both of these programs have ipod support.

---

### Post by aysiu on 2007-05-26
If you want iTunes, use AmaroK, Banshee, or Rhythmbox instead. More details here:
[http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux](http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux)

If you *need* iTunes, stick with Windows or Mac. Trying to get iTunes working in Linux is going to give you nothing but headaches at worst, or a crippled iTunes at best.

---

### Post by money2themax on 2007-12-15
dude do this get Rockbox/iPod Linux in stall that and use armaroK that will make your day trust me [ijust wish i could delete the AppleOS and back it up it's like an infection]

---

### Post by Amackera on 2007-12-15
AmaroK is the best! I wish there was a native gdm version.

---

### Post by siciliancasanova on 2007-12-15
> **Amackera said:**
> AmaroK is the best! I wish there was a native gdm version.

Exaile is supposed to be a gtk media player based off amarok.

---

### Post by money2themax on 2007-12-15
native gdm what is that?

---

### Post by lespaul_rentals on 2007-12-15
> **drakebahamut said:**
> i have the new umbuntu and i want itunes. i have installed wine and i was told it would work. but when i download itunes and try to install it a window comes up and it says     Fatle error can not load picturs  or least somthing like that can sombody help me?

It doesn't work, I've tried it.  If you do get it to work you're one lucky person, and even then it won't work well.  Just use Amarok, Rhythmbox, or Exaile, all three very qualified media players.

Oh, and also run this command in the Terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by barbedsaber on 2007-12-15
an someone please tell me which player give good mp3  support. I recently bought an LG mp3 player specificly because it supports OGG files, but it is really really annoying me, because it is designed for windows media player. please help. Thanks heaps

---

### Post by barbedsaber on 2007-12-15
Just bumping this post cause I really need the help, if this is against the rules, please tell me.

---

### Post by money2themax on 2007-12-15
amaroK that supports any USB device it tried to say my 250GB seagate External HDD was a media player but it asked before hand

---

### Post by the Didey on 2007-12-15
having a fine time with amaraok and an ipod.

amarok als supports ogg.

as someone mentioned you will need 

"commonly restricted packages" for mp3 support.....i'm about 85% sure on that one.

you can get that with an apt-get command or in synaptic

ALSO.....forget itunes. Amarok is just as intuitive......and won't hate you.

---

### Post by barbedsaber on 2007-12-15
Thanks, am downloading now.

---

### Post by rich.bradshaw on 2007-12-15
Haha, someone actually wants to run iTunes! Have you actually used it? It's awful!

As mentioned before, amaroK is the way to go.

---

### Post by barbedsaber on 2007-12-15
Its quite possible that the guy that made this thead wanted Itunes because of the Itunes store. I have heard of many similar things, but the first one tha tcomes to mind is ripit.com or somthing like that. I havn't used it myself so I cannot recomend that it is good or bad, but it may be worth a look, infact, I will check it out now.

---

### Post by money2themax on 2007-12-15
> **rich.bradshaw said:**
> Haha, someone actually wants to run iTunes! Have you actually used it? It's awful!

As mentioned before, amaroK is the way to go.

i'd use it over window media player any day and for a cooperate program it's actually pretty good

---

### Post by ericesque on 2007-12-15
I just discovered Banshee tonight.  I have to say I'm completely impressed.  Rhythmbox was having trouble playing AAC files.  I thought it was a gStreamer issue, but apparently not.  Banshee plays AAC just fine.

It has a beautiful Recommended Artists pane that seems to grab its offering from LastFM-- it's highly accurate and well thought out.

In regard to your LG player, Banshee's website says  it works with iPods and "...almost any other generic USB Mass Storage player."

Check it out for yourself:
[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

To install:  Applications >Add/Remove...    and search for Banshee  :guitar:

---

### Post by barbedsaber on 2007-12-15
I just finished the download/install of amaroK, and it looks as welcoming as well somthing not very welcoming and simple, wheras iTunes looked kinda simple, but with all the positive comments I have heard about amaroK, it must be ok, and I don't want to have to return my mp3 player, so I will go and give it a good go before I give up.

---

### Post by barbedsaber on 2007-12-15
in response to ericesque's comment, I did try banshee, (and kaffine and rythem box) but I couldn't find the mp3 player options, but if anyone has used/remembers windows media player, it had a whole tab. It was my favourite part of the entire freaking operating system!

---

### Post by siciliancasanova on 2007-12-15
> **barbedsaber said:**
> I just finished the download/install of amaroK, and it looks as welcoming as well somthing not very welcoming and simple, wheras iTunes looked kinda simple, but with all the positive comments I have heard about amaroK, it must be ok, and I don't want to have to return my mp3 player, so I will go and give it a good go before I give up.

I agree, Amarok does need a redesign, graphically and layout wise but after forcing myself to use it, and being iTunes lover on Windows, I will say that Amarok definitely has it going on for it in the guts.

---

### Post by barbedsaber on 2007-12-15
I am trying to connect my mp3 player to amoroK but really dont know what I am doing, it wants me to "configure my device and then click the connect button." Once again, the visual poulotion of the player is making finding the function I want a daunting task. PLEASE HELP.

---

### Post by the Didey on 2007-12-15
I did this.

Here's what I know for sure:

You need to set the mount point and name of the device. Then in amarok setttingg-->configure amarok--->devices you need to add the device. the you can use the connect button to get it into the side bar.


What I can't remember is exactly how I set the mount point and name. If I remember right...a window should pop up when you connect the device....and that should show the default name and mount point. you can just add those to amarok


a little help on that part?


EDIT: you could probably rename it with the **gksudo nautilus command**.

---

### Post by money2themax on 2007-12-15
> **siciliancasanova said:**
> I agree, Amarok does need a redesign, graphically and layout wise but after forcing myself to use it, and being iTunes lover on Windows, I will say that Amarok definitely has it going on for it in the guts.

iTunes lover on windows iTunes is the same on any OS that is supported by it i've used it on win and mac and i see no difference

---

### Post by lespaul_rentals on 2007-12-15
> **barbedsaber said:**
> I am trying to connect my mp3 player to amoroK but really dont know what I am doing, it wants me to "configure my device and then click the connect button." Once again, the visual poulotion of the player is making finding the function I want a daunting task. PLEASE HELP.

Does your player have a USB mode option, something along the lines of MTP/MSC?

---

### Post by SoberWarlock on 2007-12-15
Actually the newest ubuntu is Ubuntu Ultimate gaming version. It has iTunes installed on it already.

---

### Post by lespaul_rentals on 2007-12-15
> **SoberWarlock said:**
> Actually the newest ubuntu is Ubuntu Ultimate gaming version. It has iTunes installed on it already.

Actually that's a load of untruth.

---

### Post by money2themax on 2007-12-15
it sounded untrue because of what i've heard from apple on that subject

---

### Post by Ramrod_The_Wizard on 2007-12-15
Well if your problem is primarily synchronization with your ipod, just use gtkpod.  It's a really great program and does everything you need.  One word of advice, ipods do not support the .ogg filetype, which is the default filetype for music ripped from a CD, so you may want to set your default on your extracting program (most likely sound juicer).  

If you are only a beginner to linux, I would not recommend using rockbox.  Changing the firmware on the ipod is a perilous task and the risk is only compounded if you don't fully understand what you are doing.  I would try out a few media players before you decide on one because it's always best to discover things for yourself.   Personally I like Rhythmbox, though I might try out Banshee.

---

### Post by barbedsaber on 2007-12-15
in response to what was said ages ago about MSC or MTP YES IT DOES!

---

### Post by lespaul_rentals on 2007-12-16
Set it to MSC.  This will cause your computer to view it as a hard drive.  You can then drag-and-drop files to it, or if you prefer use a program such as Amarok, which will automatically detect the device and allow you to synchronize with it.

---

