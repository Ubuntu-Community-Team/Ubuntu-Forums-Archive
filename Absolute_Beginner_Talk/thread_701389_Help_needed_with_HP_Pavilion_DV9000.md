---
title: "Help needed with HP Pavilion DV9000"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by theinnercityhippy on 2008-02-19
Hello,

I threw my piggy bank from a great height on boxing day, seperated the cash from the ceramic shards and hot-footed it to PC World to purchase a HP Pavilion DV9605ea.

Having decided to purge myself of the horrible ogre that is Vista, I am now running Ubuntu Gutsy Gibbon and loving every minute of it (of which there have already been many). Everything is working to a point (even the horrible BCM43xx with ndiswrapper) but I seem to be having trouble with a few things and was wondering if there are any more experienced users out there who could steer me away from the Ubyss. Specifically, there are two main things I really need help with.

1) My audio is quite frankly crap. My lspci shows a lot of unknown devices. I'm wondering if it's something to do with the firmware for the motherboard? If I'm using software like audacity with a jack server it crackles really badly whichever sample rate I use. I'm a musician and so got this computer to edit sound files on the move. i think it's a conexant high definition audio MCP67 (is that built in to the video card)

2) As a project I'd quite like to know how to bind the multimedia keys at the top of the laptop to control audio/video events.

Thanks so much for the help the community has already given me through these forums. I've had a great time getting under the bonnet and making computing fun again. I hope there is a knight/knightess in shining armour out there somewhere! Anyway, here is my lspci if it can help find a solution:

jimdog@jimdogsbrain:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

and
jimdog@jimdogsbrain:~$ lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
00:07.0 0403: 10de:055c (rev a1)

---

### Post by benny bronx on 2008-02-19
More of a serf than a knight but I will add my two shillings until someone who actually knows what they are doing happens by..  There are two programs in synaptic that should  allow you to map your keyboard.  They are "hotkeys" and "keytouch".
  And make sure you have the correct keyboard layout in system-preferences-keyboard-layout.

---

### Post by theinnercityhippy on 2008-02-19
Thankyou good sir,

I'll try a bit of campaigning to try and get you a mention in the honours list.

Trying Keytouch now but it doesn't have my keyboard listed. Any ideas how I can import the settings I need (is there a keyboard layout file for this floating around anywhere or can I make my own to share with others)? i altered the settings successfully in System>Preferences>Keyboard>Layouts and chose 

"Hewlett-Packard SK-2501 Multimedia Keyboard".

Pressing the DVD button now brings up Rythmbox and the play, forward, back etc works great with this but the old HP quickplay button doesn't seem to do anything so I want to try and bind this to launch Rythmbox and the DVD button to launch Totem. I'll have a play with keytouch now and post any success I get.

Back to the grind...

---

### Post by Hobo Joe on 2008-02-19
What app are you wanting to bind the media keys for? It various from program to program.


As for your sound issue, paste the output of this command:

```

sudo asoundconf list

```

---

### Post by MONODA on 2008-02-19
I also have a hp pavillion laptop (dv6000) and they all have the blue light sensors at the top. Mine were detcted immidiatly but you can custumise them along with all of your keyboard shortcuts at system->preferences->keyboard shortcuts. just click on the area you want to keyfigure and press the key you want. it worked well for me.
EDIT: the default media player is rythmbox so if you configure what used to be the quickplay button to launch your media play (like i did) then it will launch your media player. you can change the media player at system->preferences->prefered applications. 
PS I suggest setting the DVD button to eject the cd rom drive :)

---

### Post by theinnercityhippy on 2008-02-19
Hiya

The output for that command gave me:

Names of available sound cards:
NVidia

I'd really like to have the quickplay button launch Rythmbox and the DVD button launch either  VLC or Totem, but it's a general guide I need as I'm going to set up a seperate user purely for using sound editing applications like Ardour and Audacity. In that environment I'll need one to launch a sequencer and one to launch an editor or something.

Tried the keyboard shortcuts but for some reason the quickplay button doesn't register when I try to use it as a new accelerator. All of the other buttons work ok though. Nothing happens when I press it in xev either :-( It was I think used specifically to bring up the quickplay program in Vista though I didn't get too into it there as I didn't want to become yet another pet of Bill Gates :-)

---

### Post by theinnercityhippy on 2008-02-19
By the way, the exact model is a HP Pavilion DV9605ea with an AMD64x2 processor if it helps at all? Don't know how many models the same laptop case/layout was used for. And just as a subtext to further boggle you all, the lspci shows an awful lot of unknown devices. Is this normal or is there a way to clear them up a bit?

Thanks again guys

---

### Post by theinnercityhippy on 2008-02-19
Right, thanks for help with hotkey bindings. I'm editing a new file in keytouch editor for the dv9000 sedries and will post it when it's done for others to use. Finally have a chance to do something for other forum users :-)

I'm binding functions for the remote control as well so I hope it will be helpful to someone.

That's one down, one to go...

---

### Post by TroyDowling on 2008-04-07
I googled around (I own a dv9013ca) and this is what I came up with.

```
sudo aptitude install linux-backports-modules-generic
```

```
sudo apt-get install linux-backports-modules
```

I'm actually just waiting for an update before I try them myself. I'll let you know how they work.

---

### Post by TroyDowling on 2008-04-07
Mm, after re-reading those guides I got commands from, I realized that the trick is for Gutsy, not Hardy. Hmm... Guess I'll wait for the pros to show up myself. =] Right now all I'm doing is customizing everything to my liking after the new install anyways. (Been battling Ubuntu to work on my Pavilion for a month now, today was my victory!)

---

### Post by theinnercityhippy on 2008-04-09
Hiya troy.
As far as I'm aware, when you updated to Hardy you will also have reconfigured the repositories so it is still worth trying the two commands above as it will try to find Hardy specific modules. I had my hotkeys working for ages but there seems to be a bug with Hardy (which is registered with launchpad already) which causes keytouch to close unexpectedly at random. Just waiting for the kernel to be updated with a fix for this.

All of the blue buttons currently work for me except the volume and mute buttons. I think this is because in Hardy there is a change in the way that audio is handled to the PulseAudio server, and therefore the commands that pressing the buttons generates are not recognised.

Once I get round to it, I'm going to look at it in more detail, feel free to message/reply me if you have any problems you need help with. I'm no expert but the last month has been a steep learning curve for me and I have got to grips a little more with how the system is operating.

Have fun :-)

Jimdog

---

### Post by TroyDowling on 2008-04-09
That's strange. The volume slider, +/- operators and the mute all worked out of the box for me. (DV9013ca). I've just never bothered to play with the other ones, though I would like to be able to launch some applications via the other buttons.

---

### Post by Kretien on 2008-04-17
Hello, I have HP Pavilion dv9000 that I just programed a keyboard layout for keytouch.  I set the defaults to control Amarok and the dvd button opens VLC but that can be changed.  I hope this helps!

---

