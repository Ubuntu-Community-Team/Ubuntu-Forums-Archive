---
title: "Sound Card Compatibility"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Haruka9250 on 2007-06-19
Hello All! I'm new to linux and really like it so far...I am having a minor issue, and here is my take on it. I don't have any sound, so i believe that the OS can't figure out what kind of sound card I have in the machine. A friend suggested that I look at the numbers on the sound card itself, and I wrote them down. My question is how can I get the operating system to recognize the sound card so that I can hear whatever is playing on the screen? thanks!

Yours Truly,
Ruthi

---

### Post by marc321 on 2007-06-19
Greetings!

I'm glad you are liking Ubuntu so far.

First of all, do you have a speaker icon in the lower left-hand corner of the screen? If so, click it and check the volume level. Maybe the sound is just muted. It's possible.  :)

If not, I am going to recommend using the command line. Type in ```
lspci
``` or, so you don't have to wade through text, ```
lspci | grep audio
```

Look for something related to multimedia audio controller.  Post up what you find (or don't find) and we'll go from there.

EDIT: Didn't notice you were using Kubuntu. My directions to get to the terminal were Ubuntu specific, but you found it anyway! :cool:

---

### Post by Haruka9250 on 2007-06-19
Ok, I don't have any sort of speaker icon. in the right-hand corner it says that the "mixer" is unavailable. I typed in both sets of commands. the " lspci" command shows some items, but I'm not really sure what they are.....the other command (grep audio) you suggested didn't do anything at all.hmmm...

---

### Post by Haruka9250 on 2007-06-19
This is the result I got, it's just copied and pasted here. maybe this will help? Thank you for doing your best to help, this is all new to me.

Ruthi



ruthi@localhost:~$ lspci | grep audio
ruthi@localhost:~$ lspci
00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03       )
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (       rev 03)
00:12.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
ruthi@localhost:~$

---

### Post by j002 on 2007-06-19
Your friend was right.

Look in 'the excerpt from the Ubuntu book'.  

If it isn't under help, you can find it above in the 'sticky' post READ HERE FIRST under 'Official Documentation' and then 'Ubuntu 6.06'.

---

### Post by marc321 on 2007-06-19
Well, it sounds like you're right.  Ubuntu isn't picking up the sound card for some reason.

Please run

```
lsmod | grep snd
```

and post up your findings.

I'm sorry I'm making this so command line intensive.  It is just the fastest way I know of to rip out only the information we need.

EDIT: You posted your lspci output before I could ask you to. Thanks! :-)

---

### Post by abn91c on 2007-06-19
in a terminal window type alsamixer, if you card was detected you get a mixer window simolar to the attached picture, play with the settings there

---

### Post by Haruka9250 on 2007-06-19
Wow...here's the result. Now I realllly don't know what this is, but here we go. :)


snd_mpu401              9256  0
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_opl3_lib           11520  0
snd_hwdep               9988  1 snd_opl3_lib
snd_cs4231_lib         26112  0
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                79876  2 snd_cs4231_lib,snd_pcm_oss
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_page_alloc         10888  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  6 snd_seq_dummy,snd_seq_oss,snd_opl3_lib,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54020  13 snd_mpu401,snd_seq_oss,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8672  1 snd
ruthi@localhost:~$

---

### Post by Haruka9250 on 2007-06-19
Here's the result from the alsamixer command:

ruthi@localhost:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
ruthi@localhost:~$


Eeek...

Ruthi

When I opened the machine, I found some numbers on the sound card itself. They are: D1696F. I don't know if that is helpful or not, but I figured I'd throw that in, just for the heck of it.

---

### Post by marc321 on 2007-06-19
Well, from what I can tell, it is a sound card based on the Crystal Semiconductor 4231 chipset.  Why Ubuntu is loading the module (driver, basically), and not showing the card in lspci is beyond me right now.  Try abn91c's advice.

:-k

EDIT: Again, I was too slow.  Sorry.  I'll have to think about this one a little more.

---

### Post by j002 on 2007-06-19
You have to modprobe manually.

You need the Brand name as well as the number of the card.

See here under "can't detect sound card" about halfway through :

[https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html](https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html)

---

### Post by Haruka9250 on 2007-06-20
Ok, i tried the first option and i was able finally pull up the mixer, however I don't know where to go from here. I cant figure out how to save this, as when I type in the command for this part:


(foo@bar:~$ sudo gedit /etc/modules )

It doesn't seem to do anything. the one that pulled a result is the snd-dummy sound card model...maybe i'm just trying to type it in wrong. where would i insert that in the command line seen above? Typing in the command as:   sudo gedit /snd-dummy/ modules  doesn't seem to do anything, however I can now pull up the alsamixer when I type that command in..mild progress I think...Now if I can just get a cd to play or something, that would rock.


Ruthi



Card: Dummy                                                                  &#9474;
&#9474; Chip: Dummy Mixer                                                            &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-9.00, -9.00]                                          &#9474;
&#9474;                                                                              &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;        80<>80        80<>80        33<>33        80<>80         0<>0         &#9474;
&#9474;      < Master >      Synth          Line           CD           Mic          &#9474;

---

### Post by j002 on 2007-06-20
Its not very clear, you have to put a line of script in the file.

When the file opens add :

modprobe themodule

on a new line, and then save it.  

To find out what you have ('themodule"), open up the PC and look for the sound card, and get the number and code on the biggest chip.  Then see if you can find it on the list from the book.

You have to restart for it to take effect.

---

### Post by Haruka9250 on 2007-06-20
Ok, great, but how do you save? lol...sorry to have to ask but i just don't know. I had to use a mirror to see under the sound card for the label, and all I could see was D1696F on a large sticker on the bottom. should I attempt to type that in, assuming I figure out how to save?

Ruthi

---

### Post by marc321 on 2007-06-20
I've been trying to look up D1696 in Google and all I can find out is that is it a number commonly associated with Hewlett-Packard hard drives.  Typing in D1696F only turns up a few Russian pages and some junk.  I don't think that is the number we need.  :)

Do you have any information on the model of the computer?  Is it brand-name?  If so, there should be some identifying marks somewhere on the outside of the case (usually front panel or back), giving a brand name, model name, model number, serial, etc. If you have that information, we can look the up the computer online and see what sound card it came with.

Loading the snd-dummy module will make alsamixer appear to work, but it only thinks it's controlling a real sound card.  In fact, snd-dummy does nothing for sound.

When the time comes to edit /etc/modules, only type in the module name (like snd-cs4231 or whatever it may be), without the "modprobe" in front.  With that done, you can set the volume in alsamixer, then run 

```
sudo alsactl store
```

to save the volume.

---

### Post by Haruka9250 on 2007-06-20
Well, this computer doesn't seem to be name band. I got it from a guy off of Craig's list when my friend got one cheap, I figured it wouldn't hurt me to get one as well, since it only cost me $13! lol. Well, on the front it says "Digital PC 3000". It has an intel pentium 2 in it, and that's about all I really could tell you about it...My friend suggested that perhaps the sound  card in it isn't the original one that came in the machine, so your guess is as good as mine. Would it be a bad idea to try and install a new sound card in it and present new problems if I did so? Or would it be simpler in the end? I don't know if there is any more info on the sound card itself, I was a little nervous to try and figure out how to remove the thing, Those aforementioned numbers were the only visible thing on the card itself, and are on the bottom of it as it is oriented in the machine. It's funny, I've taken apart Macs many times, and yet I'm hesitant to rip this thing's innards out....Let me know what you think.  :)

Ruthi

---

### Post by marc321 on 2007-06-20
Given the information we have, I think your idea of getting a new sound card is a good one.  They are inexpensive and easy to install.

Just follow these basic steps:

[LIST=1]
[*]Unplug the computer
[*]Be sure you have unplugged your speakers.
[*]Place the computer on the floor or table on its side
[*]Open the case and remove the screw securing the sound card in place
[*]While you are working in the case, **keep one hand or your forearm in contact with any metal portion of the case** to prevent static discharge to the computer.
[*]Firmly grasp the top of the card and pull up slowly. You may have to rock it back and forth to get it to come loose.  Since you'll probably get rid of the card, you don't have to worry much about touching the circuitry on it.
[/LIST]

For a new card, I would suggest any sound card with the SoundBlaster Live name.  In my experience, they are well-supported in Linux.  There are two types of add-on cards for older computers: PCI and EISA.  You will most likely want a PCI card.

Here is an image on Wikipedia of a PCI card: [PCI]("http://en.wikipedia.org/wiki/Image:32-bit_PCI_card.JPG").  An EISA card looks similar, but with larger gold contacts.

Follow the reverse of the preceding steps to install it.  Be very careful to keep a hand or arm on the case while you're working.  When you handle the new card, hold it by the edges and/or the metal bracket.  You will have to press firmly from the top while keeping the card in a good upright position to snap it in.  There is not much to worry about.  Even if you accidentally touch the circuitry on the card, or take your hand off the case for a while, you probably won't hurt anything.

There shouldn't be any other steps.  Put your case back together, plug everything in, and cross your fingers.

EDIT: Removed info about possible onboard sound. A new sound card is definitely the way to go if you don't mind spending a few more bucks.

---

### Post by Haruka9250 on 2007-06-20
Alrighty, here's the latest update: I opened the computer again, and got a closer look at the chip in it. It does indeed appear to be a Crystal sound card as you thought, but the computer just can't seem to find it when I type in either commands. Here is what was on each of the black blocks on the card itself...

1) Crystal CS4232-OK EP

WFAJAF9543

2) Wavefront
FCS2115V
9550
4A5OO245

3) ICS
IG52302Y
9616-001
F228LO

I thought that it was either a Crystal or Wavefront card,,. but the computer just can't seem to find the darn thing...also, it doesn't seem to be a pci card, I already made a pointless trip to Goodwill computer store and when I opened the machine, I realized that the two cards were quite different in size, so needless to say I figured the next course of action would be to try and get the machine to find what it already has before I make another trip back to the store to buy another sort of sound card. Hmm....any suggestions?

Ruthi

---

### Post by Haruka9250 on 2007-06-20
OK, after nosing around a bit, I have found out that ISA sound cards aren't always compatible with ubuntu, so I'm wondering if it is a lost cause, or if there is some way to put in some sort of command that will make it recognize the card. There is no way insert a pci card, so that's unfortunately not an option with this machine. If anyone has any thoughts, please feel free to share. Thanks!

Ruthi

---

### Post by marc321 on 2007-06-20
Ahh, Crystal CS4232. It's loading the CS4231 module.

Try this:

```

sudo modprobe -r snd-cs4231-lib
sudo modprobe snd-cs4232
sudo echo "snd-cs4231-lib" >> /etc/modprobe.d/blacklist

```

Try alsamixer again, turn up the volume, and try playing something.  If you get nothing, reboot and try again.

If that doesn't work, I'm about out of ideas.  Good luck!

---

### Post by Haruka9250 on 2007-06-20
Thanks so much for all your help, but I guess that this system just hates the sound card that I have. I doubt there's any way to rig one on-board somehow, but I do want to say thanks for all the time you put into replying with ideas. I wonder if there's another flavor of linux out there that might want to cooperate with it? Either way, I'm sure that it's worth giving a try for awhile and maybe I'll stumble across something of use to make it work in the future.

Many thanks for all the help and suggestions!

Ruthi

---

### Post by marc321 on 2007-06-20
Y ou're welcome.  I'm sorry we couldn't get it working.

A couple final thoughts.  If you want, you can try removing the card and reinserting it (unless you already have).  It could just be a bad connection.  Or it could just be a dead card.

At any rate, have fun with your exploration of Linux and welcome to the community!

---

### Post by Haruka9250 on 2007-07-06
Hello again everyone! A friend of mine had a fabulous sounding suggestion today for fixing my sound card issue: a usb sound card! Amazing that I had never heard of such a thing before. Is anyone here familiar with these at all? Also, if I attempt this, is there a compatibility issue that could possibly be circumvented? If anyone has any thoughts, feel free to respond. I'm willing to give this idea a try if it would be worth it.

Ruthi :KS

---

