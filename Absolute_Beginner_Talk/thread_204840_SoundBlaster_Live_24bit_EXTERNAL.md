---
title: "SoundBlaster Live 24bit EXTERNAL"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-27
hi, i have a SoundBlaster Live 24bit EXTERNAL sound card. when i go to the volume control in Windows, i can have many different inputs/outputs volume controls... including rear/front/sub volumes....

in ubuntu, i only have 1 volume control, master.. no I/O volumes...

is this just how ubuntu is?

any help would be valued...

---

### Post by shoot2kill on 2006-06-27
sorry, quick reply by accident, dnt know how to del

---

### Post by masterjonny on 2006-06-27
> in ubuntu, i only have 1 volume control, master.. no I/O volumes...


Double click the volume icon (it will be in the top right if you are running Gnome)

Go to Edit -> Preferences -> and then tick the boxes of the speakers/volumes you want to adjust and the appropriate sliders will come up.

---

### Post by shoot2kill on 2006-06-27
sorry, ubuntu, running KDE desktop.. 

sorry

---

### Post by masterjonny on 2006-06-27
Cant say I've EVER run KDE so im not to sure...I think they app you need to fiddle with is called "KMixer" though

---

### Post by shoot2kill on 2006-06-27
yes, but even in Kmix.. i still have no option of selecting any other channels...

does ubuntu have any sort of soundblaster drivers site i can go to...

??????????

---

### Post by masterjonny on 2006-06-27
Ubuntu uses the ALSA (Advanced Linux Sound Architecture) for its sound so you best bet would be looking around [the ALSA homepage]("http://www.alsa-project.org/").

And heres a [direct link to the Creative ALSA page]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs").

I dont think you can get official Creative support though because after looking around the Creative site abit I got 
"You have selected Live! 24-bit External and Linux. 
We're sorry; no Creative updates are available for the product you selected."

Good Luck :)

---

### Post by shoot2kill on 2006-06-27
hey, just forund this, but being a n00b.. i didnt understand any of it...

any help would be grateful

[http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb)](http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb)))

---

### Post by masterjonny on 2006-06-27
I dont know if its just me but clicking that link gets me 

"HOWTO Install Creative Sound Blaster Live 24-bit external (usb
There is currently no text in this page, you can search for this page title in other pages or edit this page."

Copied the link wrong?

EDIT: It works now...jus summat weird :/

---

### Post by shoot2kill on 2006-06-27
yes i did, but updated now.. try again

---

### Post by masterjonny on 2006-06-27
The first bit is about emerging the drivers into the kernel, which is more a Gentoo thing than a Ubuntu thing (nasty OS Gentoo is).

Im going to presume that your Sound does work and you dont need the driver installation explaining, so onto configuring.

Goto you home folder ( /home/username), in any file browser you like and create a new .asoundrc file there. Open that file with a text editor, such as Kate and paste into it,

```
pcm.usb-audio {
           type hw
           card 0
        }

ctl.usb-audio {
           type hw
           card 0
        }

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dsp0 {
        type plug
        slave.pcm "dmixer"
}


pcm.dmixer {
        type dmix
        ipc_key 1025 # Should be a unique number
        slave {
                pcm "hw:0"
    }
    bindings {
           0 0
           1 1
    }
}
```

I will give you a word of warning though, I once created a .asoundrc file for my sound card (Audigy 2) and Ubuntu promptly refused to boot...so be careful.

Also at the bottom of the page he mentions an ALSA patch for USB sound cards, so youll have to try and find on ALSA's site and apply it....you could also try searching in Synaptic for it, it wouldnt suprise me if it was on there.

Any more problems just keep posting, well get this working :)

---

### Post by leisuresuitgreg on 2007-07-11
I realise this is a year later, but I used these above instructions and it works perfectly. I can now run Skype and Jack etc... with the my Dell Inspiron 1300 Laptop and still use the on board sound card if I need to.

Cheers

Greg

---

