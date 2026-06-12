---
title: "[SOLVED] trying to install flash"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by kaysersoze on 2007-09-02
Hello.

I have downloaded the flash9 installer from the Adobe website (install_flash_player9.tar.gz). I have extracted the file and on the terminal typed ```
sudo flashplayer-installer
```

It asked for confirmation if I want to continue with the installation so I hit ENTER to continue. It then prompted me with the following:

> Please enter the installation path of the Mozilla, SeaMonkey or Firefox browser:

What do I enter as path? I am running Ubuntu 7.04 default install.

In windows, almost all programs are usually located in C:\Program Files folder. How do I know the path of the different programs in Ubuntu?

Thanks.

---

### Post by ThrobbingBrain66 on 2007-09-02
You're making this too hard on yourself :)

Assuming you have the multiverse and universe repos enabled (System > Administration > Software Sources > Tick the boxes for multiverse and universe)

After you close that window, fire up a terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by rspaulding on 2007-09-02
> **ThrobbingBrain66 said:**
> You're making this too hard on yourself :)

Assuming you have the multiverse and universe repos enabled (System > Administration > Software Sources > Tick the boxes for multiverse and universe)

After you close that window, fire up a terminal:
```
sudo apt-get install flashplugin-nonfree
```
this did not work for me...  i got this error:
```
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

```

---

### Post by gmjs on 2007-09-02
From memory, the path you want is /usr/lib/firefox/firefox.

I will check this for you when I can access my Linux box!  There's no harm in trying it though.

Graham

---

### Post by Sef on 2007-09-02
Use Applications > Add/Remove to install the flash plugin.

---

### Post by Duck2006 on 2007-09-02
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

This may help

---

### Post by peebly on 2007-09-02
> **kaysersoze said:**
> Hello.

I have downloaded the flash9 installer from the Adobe website (install_flash_player9.tar.gz). I have extracted the file and on the terminal typed ```
sudo flashplayer-installer
```

It asked for confirmation if I want to continue with the installation so I hit ENTER to continue. It then prompted me with the following:



What do I enter as path? I am running Ubuntu 7.04 default install.

In windows, almost all programs are usually located in C:\Program Files folder. How do I know the path of the different programs in Ubuntu?

Thanks.

double click on flashplayer-installer and select run in terminal, now follow the on screen instructions.

:)

---

### Post by ThrobbingBrain66 on 2007-09-02
> **rspaulding said:**
> this did not work for me...  i got this error:
```
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

```

You have to make sure that the universe and multiverse repos are enabled.  This only works if you have a 32-bit install of Feisty though.  For 64-bit installation, use the following guide:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by FuturePilot on 2007-09-02
The path is /usr/lib/firefox
But as others have mentioned, you can also install it via Synaptic or Add/Remove. That way, you'll also be kept up-to-date.

---

### Post by kaysersoze on 2007-09-04
> **FuturePilot said:**
> The path is /usr/lib/firefox
But as others have mentioned, you can also install it via Synaptic or Add/Remove. That way, you'll also be kept up-to-date.

I typed the /usr/lib/firefox path and it continued with the installation. I run the browser and I confirmed that flash plugin is now installed.

Thanks for all the responses.

---

