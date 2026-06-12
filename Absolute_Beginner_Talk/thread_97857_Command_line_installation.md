---
title: "Command line installation"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Doomed_Tupperware on 2005-12-01
Um I know that you can install stuff from apt-get and the synaptic package manager, but I would also know how to install programs manually from the command line. I tried to install the flash plugin for Mozilla, but I couldn't get the instructions in the readme...

"To install the Plug-in Player for Linux via an install script, follow these directions:

- This installer is script-based and cannot be run from a GUI.

- Uncompress install_flash_player_7_linux.tar.gz. A directory called install_flash_player_7_linux is created. Navigate to this directory.

- From the command line, type ./flashplayer-installer to run the installer. The installer will instruct you to shut down your browser(s).

- Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, choose Help > About Plug-ins from the browser's menu."

But, when I run that in the terminal it says "no such directory"

Any help would be very much appriciated.

---

### Post by invalid on 2005-12-01
When you run what command? It should be something like this:
```
tar xvfz install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
chmod +x flashplayer-installer
./flashplayer-installer
```

You may need to use sudo, depending on where it is located, and where it installs to.

Cheers,
Cb

---

### Post by Doomed_Tupperware on 2005-12-01
[QUOTE=invalid]When you run what command? It should be something like this:
```
tar xvfz install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
chmod +x flashplayer-installer
./flashplayer-installer
```

You may need to use sudo, depending on where it is located, and where it installs to.

Cheers,
Cb[/QUOTE]

./flashplayer-installer, that command. Would you mind explaining what all those commands actually mean to the computer?

---

### Post by gruepig on 2005-12-01
```
tar xvfz install_flash_player_7_linux.tar.gz
```

This expands the downloaded file.  Think unzip.

install_flash_player_7_linux.tar.gz is a gzipped tar file.  A tar file (tarball) is an archive of a bunch of files made into one larger file.  gzip compresses (more efficiently stores) the archive file.  The command to tar/untar archive files is tar.  The options 'xvfz' mean to Verbosely eXtract the gZipped Files.

After you've run tar, you can use ls to list the directory contents (like dir in dos).  Try 'ls install_flash_player_7_linux'.  You should see a bunch of files.

```
cd install_flash_player_7_linux
```

cd is a bash builtin command to Change Directories, so this changes your directory (folder) to the newly-created directory, install_flash_player_7_linux.

```
chmod +x flashplayer-installer
```

chmod change the file modes (that is, permissions).  Here you are adding eXecute (run) privileges on the file flashplayer-installer.  If you don't do this, you won't be able to run the file.

After doing  this, run 'ls -l flashplayer-installer' to list the file information in long format.  This should show the file name and file permissions (r for read, w for write, and x for execute), along with the file's owners (user and group), size, etc.

```
./flashplayer-installer
```

Run the executable flashplayer-installer.

. is your current directory, so you use ./<filename> to run a file named <filename> in the current directory.

In general, if you want to know what a command does, you can run 'man <command>' to read the manual.

---

### Post by invalid on 2005-12-01
Could not have explained it any better myself :)

Cheers,
Cb

---

### Post by arphe_el on 2005-12-02
you mean you want flashplayer to run to your firefox web browser?

base on my experience i just click the browser and goto site [http://www.shockwave.com/sw/home/](http://www.shockwave.com/sw/home/)

you will be prompted for the additional plugins and then click on that plugin right at the website and it will automatically install by selecting agree radio button then click next and finish. hope this helps:-)

---

