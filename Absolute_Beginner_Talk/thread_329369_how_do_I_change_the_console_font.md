---
title: "how do I change the console font?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by dfm21 on 2007-01-01
Hi!

How can I change the default console font?

_Motivation_
When ubuntu starts (without usplash), startup messages are displayed in a nice-looking font. Then the following message appears: "Setting up console font and keymap..." and an ugly font is loaded.
I want to get the standard font back.

_Questions_
[LIST]
[*]Is there an easy way to select the default console font like "dpkg-reconfigure something"?
[*]How does **setupcon** work?
[*]Is this "console-font-setting" distribution dependent? Where can I get more information?
[/LIST]
_Some clues so far_
Obviously this message comes from the boot script **/etc/init.d/console-setup**:
```

...
                log_begin_msg "Setting up console font and keymap..."
                if setupcon --force; then
...

```
So **/bin/setupcon** is responsible for setting the console font. Since it is invoked with the parameters *--force* only, I guess it gets the desired font from a config file. Unfortunately, setupcon has no manpage (there is a [bug]("https://launchpad.net/distros/ubuntu/+source/console-setup/+bug/60598") filed already), so I was unable to determine where the config file for setupcon is located (if there is any).


I hope, there is an easy way to solve this, but would also like to hear about other ways...
Many thanks in advance!

---

### Post by adaptr on 2007-01-01
You're obviously investigating, which is good... :)
I have no idea what this "setupcon" is that you mention.. it is not installed on my system (Edgy).

The first set of scripts run when Ubuntu starts up are the ones in [COLOR=SeaGreen]/etc/rcS.d/[/COLOR] - the last one of these is** console-screen**.
If you open that file with **less** or any other text editor, you'll see that it is responsible for initializing the console-tools package, which takes care of console fonts and keyboard mappings and the like.
Its configuration lives in [COLOR=SeaGreen]/etc/console-tools/config[/COLOR]; read through that to see what can be changed.
As you can see at the end of the config file, you can set different fonts for each console.

---

### Post by dfm21 on 2007-01-02
Thanks - I will keep that in mind :)

It's strange... I'm on Edgy too and the beginning of my **/etc/rcS.d/console-screen** file looks like this:
```

# If setupcon is present, then we've been superseded by console-setup.
if type setupcon >/dev/null 2>&1; then
    exit 0
fi

```
Though I can't remember having installed anything console related, the file is present on my system. Anyway, hoping that setupcon also uses **/etc/console-tools/config**, I commented out the fonts at the end, but got no effect... :(
I hope that the no-man-page-bug will be resolved soon.

By the way: How do you get this nice green font for highlighting code/files? You don't choose color in the drop down always, do you?

---

### Post by McDuff on 2007-01-17
it took me some time, but finally i found out which file to manipulate. it's /etc/default/console-setup
this file is quite self-explanatory.
i only wonder, why it was so difficult to find this solution...

---

### Post by Fnyar on 2007-03-06
Well, it's not exactly self explanatory. To be clear, here's what I had to modify in /etc/default/console-setup:

1. Change the CODESET="Uni1" line to "CODESET=Lat15". This is the default for Ubuntu Server. If you leave the codeset as Uni1 certain symbols won't display properly, like the apostrophe in man pages.

2. Change FONTFACE="Fixed" to FONTFACE="VGA". Again, this is the default in Ubuntu Server.

With these two changes in place, reboot. You might be able to get away with running whatever init script sets the console font...but my limited experimentation didn't reveal what script that would be.

---

### Post by dfm21 on 2007-07-03
Thank you so much!
That's exacly what I wanted.
I changed
```
FONTFACE="Fixed"
```
to
```
FONTFACE="VGA"
```
so there's no font change during boot.
Thanks again!


so long...

Felix

PS: Sorry for not replying earlier, but I lost track of this thread during mail-account-migration.

---

### Post by scorp123 on 2008-05-12
I tried editing the **/etc/default/console-setup** file ... but it did not really help. It seems that this is the correct way to do it: ```
sudo dpkg-reconfigure console-setup
```

You will be asked a few questions about your keyboard (e.g. the language) and a few other things, and then towards the end you will be asked about your font preferences for text consoles. So you should be on a text console (e.g. by pressing CTRL+ALT+F2) when executing this command, because then it will show the new chosen font immediately: Whatever font you selected will instantly become active. So if you're not happy with the choice you could repeat the command above and try out another font.

CTRL+ALT+F7 takes you back to your GUI session (where e.g. GDM, Gnome or KDE should be running).

---

