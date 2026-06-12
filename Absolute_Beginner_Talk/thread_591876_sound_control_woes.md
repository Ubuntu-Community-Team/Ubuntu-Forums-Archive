---
title: "sound control woes"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by rob worley on 2007-10-25
I installed Ubuntu 7.04 on a Dell Dimension xps r350 computer and have upgraded to 7.10 over the internet.  I mucked through the printer driver minefield but have been unable to get any sound.  My volume control button is x'd out and when I try to turn it on I get "no volume control GStreamer plugins and /or devices found".  I added the ugly package plugins in Synaptic Package Mangager but it did not help the situation.  I added an old sound card an that did not help.  It worked in old W2K and in original W95.  I am totally new to this but I see hope.  My children think the computer is broke if it will not play music and have sound with videos.  I should have went with less operating system like xubuntu.  It is not a problem but I have to manually shut down the computer because the bios is pre 2000 and it does not manage the ACPI.   I would appreciate any help you might give me but I don't think I can write any code etc.

---

### Post by chrisTGc on 2007-11-05
Hullo Rob,

You wont have to write code to fix problems in Ubuntu.

To start with go on to System>Preferences>Sound and under Default Mixer Tracks,Device what does that say?.Also check your soundcard setting in the BIOS to make sure it is not disabled unless you intend to retain your add in card.And was,or is the add in soundcard PCI or ISA ?.ISA prob will not work without recompiling the kernel a PCI card should.

So if you are still about let us know re the 2 items above.

Best Wishes Chris.

---

### Post by rob worley on 2007-11-14
Nothing under default mixer tracks.  My sound was enabled in bios.  I do not have a sound card - it is integrated on motherboard.  I just got my computer out and am trying to work it again.  I tried a gnome volume control command but nothing but an error message on no GStreamer plugins or devices found.  I had some updates today and there was an error on part of the music box that did not allow it to install.  System is nice but sound and printer problems.  Video is much clearer than Windows.  All of the sound checks failed above the mixer tracks.

---

### Post by rob worley on 2007-11-14
I am sorry.  I took the sound card back out.  It was probably an ISA card 486 era.

---

### Post by chrisTGc on 2007-11-15
Hullo Again Rob,

Good to hear you are still about.

Well we will try to get your sound working.I had a quick look over the R350 at Dell's site and there have been at least 4 sound systems associated with the computer ranging from Altec Lansing through Creative to Crystal.So first thing is to try find out what the sound sys is on your particular machine.So;

Open up a terminal i.e Applications>Accessories>Terminal and type in  lspci  .That in full means 'list pci hardware'.Please note first character of lspci is lower case L.What does it say,.Also look over System>Preferences>Hardware Information and scroll through the output to see if anything else is known by the system re the sound.

Let us know,Best Wishes Chris.

---

### Post by rob worley on 2007-11-15
Highlighting WDC WD 400... gives device   "storage" "block"    Capabilities :  storage,block

Crystal semiconductor CS4     CS4610/11 [Crystal Clear Sound Fusion Audio Accelerator] rev 01)   AT- Style speaker Sound   WDC   WD 400BB-00
                                                   Volume   volume (ext 3)  Volume (swap)     

Under advanced tab
  block.device string  k /dev/sda
  Storage Serial      string   1ATA_WDC_WD40....
  bloc.is_volume      bool   false  (changeable to true)
  Storage.automount_enabled_hint     bool under type and value was false.

the codecs were Crystal Fusion as they were in windows.  I had to work around them when changed it to W2K downloaded some drivers etc.  They were vintage W95.  My guess is some of the falses under value need to be changed to true?  I did not try it.  Thanks for the help.  I appreciate it.  I hope the above info helps.

---

### Post by chrisTGc on 2007-11-15
Hi Rob,

No don't change anything just yet.There is enough detail in what you have just posted to find what the prob is.But much of the info posted is about your hard disc ! .

Here is a link that says a good bit re CS4610 sound in Linux.

[http://www.thinkwiki.org/wiki/CS4610](http://www.thinkwiki.org/wiki/CS4610)

There is also a link there to the CS4239 chip (which pairs the CS4610) with more info and 2 command line inputs to terminal,try those commands with sudo.But it looks as if only the 16bit ISA CS4239 chip will work in Linux and as thats an ISA chip i dont think you will get it working with the current Linux kernel.

Another idea is;do you have a spare PCI slot?.I have a couple spare Ensoniq PCI sound cards and if you are in UK i could post one of to you. 

Let me know,Best Wishes Chris.

---

### Post by rob worley on 2007-11-16
I was lost on the pairing lines etc. with SUDO.  It sounds like the chip is lost on the current linux kernel.  I am in the US.  I have a couple of sound cards that are both ISA.  I have two PCI slots left.  My video card has the AGP slot. I tried the ISA card route without any success.  What would happen if I moved the hard drive from the Dell to a newer Compaq computer?  Or does that need to be installed on that computer?  Could I look for any PCI sound cards with linux drivers to install on the Dell?

---

### Post by chrisTGc on 2007-11-16
Hullo Rob,

You could transfer the hard drive to a newer computer.GNU/Linux is more flexible than MS operating systems in that respect.You will have to reconfigure X for a different video card and monitor.And to get sound going from System>Preferences>Sound.I have often changed motherboards on this machine without re-installing Ubuntu and despite some small hitches all has been well.So let me know if you decide to do that and i will pass a couple of tips along.But prob still best to do a clean install of Ubuntu.I assume you want to keep the compaq hard drive as it is.

Almost any PCI sound card should work on GNU/Linux.And unlike MS it should not be necessary to install drivers.ALSA (advanced linux sound assoc.) should work O.K. with near any PCI sound card.If you end up needing a PCI card i can still send one out to the States i happen to have 4 computers and a cupboard full of spares all gathering dust.You would be welcome to one.But the post would take a while to arrive.

It looks very much to me as if none of your efforts so far to get sound going on your Dell will come to much since all hardware have been ISA based.BUT there is one thing left to try;

Open a terminal up and type in exactly this;

sudo  gedit  /etc/modprobe.d/blacklist-oss

Then scroll through that text file and look for the 4 lines starting with CS  i.e CS4232 CS4281 CS461X CS46XX and put a # as first character of each of those lines so CS4232 will now look like #CS4232.Then reboot.Then go onto System>Preferences>Sound and selecting the music and video field see if the OSS sytem is available.If it is select that and click test.

Let me know if that does anything.Best Wishes Chris.

---

### Post by rob worley on 2007-11-16
Did what you said.  The OSS was available but when I did the test I got the following message:

  audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

I ordered a sound card this afternoon.  It was listed as Linux compatible and may have software - i did not ask.  It was only 20 dollars.  It was a PCI with less than 350 mhz required and I had more memory than it required..  It won't be in til next week or later with Thanksgiving Holiday next week in the US.  Do I need to unto the # character?  Thanks again for the help.  I thnk the sound card should work.  I would have to disable the sound in bios I assume. Thanks again.

The following message is what I get when I click on sound icon to turn sound on:

 " The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

### Post by chrisTGc on 2007-11-16
Hi Rob,

Yes you better take the # character back out.The black list is there for a reason,prob OSS is taken out of the Kernel maybe to avoid conflicts with Alsa.Shame this did'nt work and was the best chance we had.

Well your new PCI card should do the trick O.K. so good luck and hope you find it works well.Keep posting if you get probs.

And yes again,when you install your new PCI sound card you will need to disable the integrated sound in the BIOS.Poss conflict else.Also the onboard sound will still waste some resources unless disabled.

Best Wishes Chris.

---

### Post by rob worley on 2007-11-22
Chris, I put the sound card in last night and there were no problems except I put the speaker plug in the old place.  After I figured that out it was clear sailing.  The "Dixie Chicks" are singing right now.  Not my cup of tea either but it was handy..  Thanks for the help.  I may have done the same thing when I did the ISA sound card except I did not figure it out.  The sound card is named "Sound Card".  It is a 6-channel 5.1 Sound 3D PCI Sound card..  It was for IBM compatible PC with 32 bit PCI slot.  It was for win 95 through XP and included Linux.  It came with drivers but they were not needed.  It recommended Pentium 11 366 MHz or above.  I only had 350 MHz, but it works fine.  As we say in Arkansas, "another white belly up."   It means another job finished.  As when one kills a Rat snake it rolls over and it's while belly shows.  At any rate I am thankful for your generous help.  Ubuntu is a very nice OS allowing a lot of function on a a relatively limited computer.  I will be migrating some of my other systems when the expensive AV programs run out.  As we give thanks in this country for Thanksgiving Holiday I am indeed thankful for a very skilled and willing to share Brit named Chris.

---

### Post by chrisTGc on 2007-11-24
Hi Rob,

You are welcome and just in case nobody has said to you 'welcome to the GNU/Linux community' i will say so now.

Glad the PCI sound card is working and here's hoping yourself and family enjoy the machine even more so now.*Dixie Cups included ! *.

So the prob was the ISA sound sys.No surprise with that.It would not have mattered where you jacked the speaker leads.Funny this was the first and one of the only prob i have ever had with drivers in GNU/Linux.That machine runs Yamaha ISA sound and needs a kernel module to be compiled and inserted for it.Not easy and i havent done so yet.One day maybe.

So best Wishes to you and family and hope you had a lovely Thanksgiving.

Chris.

---

