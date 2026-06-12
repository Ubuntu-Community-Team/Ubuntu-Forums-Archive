---
title: "[SOLVED] Can't install Eclipse"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by rogdawg on 2007-10-21
I have just installed Ubuntu 7.1 (Gutsy Gibbon), and I am trying to install Eclipse. I first attempted the installation using the Add/Remove Applications utility. I get the following error.

[COLOR="Red"]Cannot install 'eclipse'

This application conflicts with other installed software. To install 'eclipse' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
[/COLOR]


So, when I go to synaptic to try to install eclipse, I get the following message:
Could not mark all packages for installation or upgrade

[COLOR="Red"]The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
eclipse:

Depends: eclipse-jdt but is not going to be installed
Depends: elcipse-pde but is not going to be installed
Depends: elcipse-source but is not going to be installed[/COLOR]

In Setting > Repository, I have, on the Ubuntu Software tab, universe and multiverse sellected. On the Third-Party Software tab, I have [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu), and [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) selected.

Any suggestions? Is there more information I can provide? I am essentially a novice/hobbiest on Linux, and as I said, Ubuntu is completely new to me (though I have played with SUSE for a couple of years). I am an advanced MS Windows user-programmer. 

Thanks, in advance, for any help you can provide.

---

### Post by Beggar on 2007-10-21
"Depends: eclipse-jdt but is not going to be installed
Depends: elcipse-pde but is not going to be installed
Depends: elcipse-source but is not going to be installed"

Looks like someone laks spleling skilz.

try running 
```

sudo apt-get update
sudo apt-get install eclipse

```

For some reason eclipse is looking for the wrong packages, a mispelled version, elcipse*. This will update your package info, which should hopefully rectify the situation.

Since eclipse is written in java, I would just download the latest version from the [eclipse site]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20070927/eclipse-java-europa-fall-linux-gtk.tar.gz"), it works fine for me.

---

### Post by rogdawg on 2007-10-22
thanks for the reply.

The spelling error is mine. It isn't misspelled in the message I received.

I downloaded the version from eclipse, and haven't had any luck getting it installed. But, I will keep trying (ugh). Then I will try to figure out how to get the Flash plug-in for Firefox...that isn't working either (ugh again).

thanks again.

---

### Post by Beggar on 2007-10-22
What problem did you have with installing it? All you have to do is extract it, and your done...

As far as the flash plugin, are you using flashplugin-nonfree?

---

### Post by Nicolas of Cusa on 2008-01-05
Just for the record. You should try this: System, Administration, Synaptic Package Manager -- then go to Settings, Repositories -- Under the Ubuntu software tab make sure that "main", "universe", "multiverse" and "restricted" are selected. Close the window and hit "reload". Try installing Eclipse again. 

Thanks.

---

