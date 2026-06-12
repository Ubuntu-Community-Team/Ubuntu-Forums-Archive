---
title: "Help!!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mixtri on 2007-05-30
Hi Guys. I have just installed ubuntu 7.0.4 on my computer which also runs winxp. I installed ubuntu on a second disk on the machine and use its dual boot feature to boot to either ubuntu or windows.

My immediate problem is trying to connect to the internet and play music.

I use a generic Adsl Usb modem which connects under windows using connexant drivers; of which i believe ubuntu support. Ubuntu seems to have identified the modem in the devicemanager console as well as other hardware including my creative soundcard.

Usinf sound juicer i am able to play cds etc but there is no sound. Also the network connections in ubuntu says there is no network connection. I have tried configuring network tools with my modem details, but no joy. Can anyone help. 
P.s i downloaded cnxinstall.run driver for usb modems and unable to run in a terminal as i get the message unable to run the file. Is there anyway that ubuntu detects hardware and gives u a list of options to remedy rather than have to learn all the technical stuiff involved in getting stuff to work. I want to use this OS but I dont feel i need to know everything about the command line programming aspect of it to get it to work.
Please help!!

---

### Post by steevols on 2007-05-30
I don't know about the modem, but with your CD player, I'd say you're soundcard is not connected to your CD drive. This seems likely, as your soundcard is likely an aftermarket upgrade. If you did not connect a small cable between your card and drive, you could try using a software-based CD player like GXine to see if you can get any audio.

---

### Post by meborc on 2007-05-30
are you supposed to insert login and password in windows to get adsl connected? if so you need to run "sudo pppoeconf" in the terminal (insert your ubuntu password when prompt)... then follow the instructions to set your adsl connection up

if you have a router between the modem and the computer you can just try to run "sudo dhclient"... try those...

these suggestions will work if your network card is recognized... to see if it is run "ifconfig" in terminal... the output should have at least 2 sections... one starting with LO and another with ETH0 (or similar)

report back if having troubles...

---

### Post by Crafty Kisses on 2007-05-30
> **mixtri said:**
> Hi Guys. I have just installed ubuntu 7.0.4 on my computer which also runs winxp. I installed ubuntu on a second disk on the machine and use its dual boot feature to boot to either ubuntu or windows.

My immediate problem is trying to connect to the internet and play music.

I use a generic Adsl Usb modem which connects under windows using connexant drivers; of which i believe ubuntu support. Ubuntu seems to have identified the modem in the devicemanager console as well as other hardware including my creative soundcard.

Usinf sound juicer i am able to play cds etc but there is no sound. Also the network connections in ubuntu says there is no network connection. I have tried configuring network tools with my modem details, but no joy. Can anyone help. 
P.s i downloaded cnxinstall.run driver for usb modems and unable to run in a terminal as i get the message unable to run the file. Is there anyway that ubuntu detects hardware and gives u a list of options to remedy rather than have to learn all the technical stuiff involved in getting stuff to work. I want to use this OS but I dont feel i need to know everything about the command line programming aspect of it to get it to work.
Please help!!

If you're super new to Ubuntu, you should download a program called "Automatix"

You can download this at: [http://getautomatix.com]("http://getautomatix.com")

Choose the install codecs (MPlayer and FF Plugin) and you should be able to play your songs.

Again Automatix is not recommended for everything.

---

### Post by Sparkster185 on 2007-05-30
Do you have sound in other applications?  Is it only missing when you play audio CDs?

---

### Post by mixtri on 2007-05-30
Hello and thanks for taking time to respond.
I do not have sound in other application - i.e all apps running when logged into ubuntu - all works fine when in windows.
Someone mentioned that I may not have the cable linking cd to card. they are both connected. I have tried unmuting also.
Its strange that ubuntu detects the card, yet plays no music.

---

### Post by rgraves22 on 2007-05-30
I would search in Synaptic for sound codecs.. I ran into a similar problem when trying to burn an Mp3.. I had to copy it across the network to my windows box, convert it to OGG than copy it back to my ubuntu laptop.. it burned fine, and played fine. It sounds to me like its a codec issue.

---

### Post by mixtri on 2007-05-30
thanks Meborc.  I don't have a netwrok card installed - [I] tried "sudo pppoeconf" but got message no ethernet card or something. the modem is the only item on the list in netwrok tools screen. i have all the right parameters fed in, but nothing. i'll give it another bash, just read some stuff in the documentation folder. thanks guys!! ;)

---

### Post by mixtri on 2007-05-30
i'll give it a bash rgraves. its just a little frustrating trying to get stuff to work, especially when the info u need is on the net and have to keep rebooting between OS's to get it. At least i'm learning new stuff:)

---

### Post by Sparkster185 on 2007-05-30
If your sound doesn't work at all it's gotta be a problem with the driver.

What sound card do you have?  Type

```

lspci -v | less

```
 
and scroll down until you find the Audio device.  (You can search through the text by pressing '/', typing in "Audio" and hit enter.  To get to the next result, hit 'n'.)

If you have an Intel HDA sound card, I know how to fix it.

---

### Post by mixtri on 2007-05-30
Hi Codename. I've looked everywhere for automatix and cant seem to find a download link. I looked on the automatix website as well as googling it. everyone seems to talk about it but forgetr to leave a link to the damned thing. Could you help?

---

### Post by mixtri on 2007-05-30
Hey Sparkster - ubuntu seems to recognise my s/card which is an EMU 1212m. I have checked and it is supported. I also have an onboard AC97 soundcard which i have disabled in the bios as it conflicts with the creative EMU soundcard in windows xp. I've been trying to get this to work for 2 days now. I'll soldier on, but i must confess using ubuntu is somewhat disheartening right now.

---

### Post by flossgeek on 2007-05-30
Don't give up, browsing this thread there could be lots of issues to your sound problem. First go to System>Preferences>Sound and click the "Sounds" tab. Click "play" button on the log out section, do you hear anything?

If you do hear something then your CD's are not likely playing due to not having the appropriate codecs installed. 

If you do hear a sound though from the Sound Preferences, but not the cd player,open a terminal and type "alsamixer" and check your channels are raised or not muted. 

Try these and let me know where you stand, and we will take it from there....

---

### Post by mixtri on 2007-05-30
hi Floss. Tried all those; to no avail.  I perform the soundcheck which generates a dialogu box which only goes so far; but i hear no sound. the only option it has is to close the box. it doesnt say yes or no to something being wrong. i'm just left there wondering what to do next. It hardly intuitive with no feedback whatsoever.

---

### Post by flossgeek on 2007-05-31
Do you have a soundblaster card in your machine?

---

