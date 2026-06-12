---
title: "I want to make a custom button"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-11-11
I have just installed edgy and got my wireless working with ndiswrapper after hours and hours messing with that and bcm43xx-fwcutter.  Anyway, to turn off the wireless card i use "sudo rmmod ndiswrapper" and to turn it on i use "sudo modprobe ndiswrapper".  I've made two custom application launchers, one for each command, and put them on my panel.  It works prefectly.  But, i was wondering if there was a way to make one button that would do this???:confused: ??? p.s. i use gnome.

note: I am not sure what to search for, so i am starting a thread.  also, i am not sure what sub-section of the forums to post this in, so i'm posting it here.  if you know of a better place, please let me know.

---

### Post by Epperly on 2006-11-11
can't you separate the applications by commas or hyphen or something? so that you'll get two applications launched at once instead of two launchers for one thing each.

---

### Post by aysiu on 2006-11-11
If there were an easy way to tell if ndiswrapper were already running, you could create a script with some if/then statements in it that would launch the appropriate command.

You could, as a weird workaround, create a little "on/off switch" (phony directory). First, create the script: ```
sudo nano /usr/local/bin/ndiswrappertoggle
``` Then put in this code in the script: ```
#!/bin/bash
if [ -d ~/.ndiswrapperon ]; then
        sudo rmmod ndiswrapper
        rmdir ~/.ndiswrapperon
else
        sudo modprobe ndiswrapper
        mkdir ~/.ndiswrapperon
fi
``` Save the script (Control-X, Y, Enter) 

Finally, make the script executable: ```
sudo chmod +x /usr/local/bin/ndiswrappertoggle
``` Then make your launcher use the command ```
ndiswrappertoggle
``` The script basically says "If the /home/*username*/.ndiswrapperon directory exists, turn off ndiswrapper and then delete the directory; otherwise, turn on ndiswrapper and make the directory."

---

### Post by insub2 on 2006-11-11
aysiu,
That worked so nice.  thank you very much, you have been most helpful.  and so prompt. thank you again.

...there wouldn't be any (easy) way to make it change the icon depending on the state, would there?

---

### Post by aysiu on 2006-11-11
Possibly... but it may involve refreshing your entire Gnome panel...

Can you post the output of these commands? ```
cd ~/.gnome2/panel2.d/default/launchers
ls
```

---

### Post by insub2 on 2006-11-11
> **aysiu said:**
> Possibly... but it may involve refreshing your entire Gnome panel...

Can you post the output of these commands? ```
cd ~/.gnome2/panel2.d/default/launchers
ls
```

sure, here it is ```
bar-0028d6f638.desktop      frobate-00e1bc6203.desktop
blah-003a047dbc.desktop     gegl-0069981cbe.desktop
blah-00aea528ac.desktop     greasy-00252e3005.desktop
frobate-00674352d8.desktop  greasy-003eec9ac7.desktop
frobate-006c035741.desktop  larry-00775f3093.desktop

```

---

### Post by aysiu on 2006-11-11
Any idea which ones has the *ndiswrapper* script command in it?

---

### Post by insub2 on 2006-11-12
> **aysiu said:**
> Any idea which ones has the *ndiswrapper* script command in it?

no.  i have no idea.

this is no longer "easy."  thank you for you help, but i will be satisfied with the unchanging icon.

---

