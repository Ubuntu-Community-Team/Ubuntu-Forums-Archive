---
title: "How can I see what sound card I'm using or any hardware for that matter in Xubuntu."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-02-24
Windows has device manager... what does xubuntu have? I can find and edit all my hardware information on my laptop with Ubuntu installed, but as my charger has bitten the dust I can't exactly hop on it and check at the moment. Does Xubuntu come with some kind of hardware manager? The onboard sound of this computer has worked with Xubuntu before, but after reinstalling it, it kept working then not working and so on and so forth, so I figured that there's a problem with the audio jack on the onboard so I popped in a sound card and now I don't know how to have Xubuntu recognize it. I'm assuming it is set to use my onboard, but I'd like to switch that and do not know how. Any help would be greatly appreciated.

---

### Post by northern lights on 2008-02-25
The command "lspci" lists all PCI devices. To see what options apply, run "lspci --help". For the soundcard specific question, you can also enter ```
cat /proc/asound/cards
``` in a terminal.

---

### Post by jordanmthomas on 2008-02-25
What northern lights suggests is good.
I also like lshw, it's a very nice piece of software:
```
sudo lshw -class multimedia
```
will show you information about your sound card, including what modules it's using, etc.

(I'm not sure if lshw is installed in Xubuntu, but it should be in the repositories if it isn't)

---

### Post by northern lights on 2008-02-25
Jordan -

just ran lshw - great little app!

---

### Post by whoscheesemine on 2008-03-01
lspci helped me with everyone I was working on thanks a million!

I haven't tried your's yet Jordan, but when I have some time I'll check it out.

Thanks a million you guys.

With an amazing helpful community like this I'm sure that Ubuntu could be just as comfortable for nonusers as Windows for them. Maybe one day you'll be able to click a model of computer you have on [www.hardware4linux.info](www.hardware4linux.info) and download everything you need for Ubuntu to work perfectly on that machine.... ahh a guy can dream right?

---

### Post by louieb on 2008-03-01
List your hardware in your browser. Easy to read:
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

---

