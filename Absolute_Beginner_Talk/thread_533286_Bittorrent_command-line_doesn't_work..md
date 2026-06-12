---
title: "Bittorrent command-line doesn't work."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-23
I tried a guide I found on Google for bittorrent command line. I got the .deb but hit some dependency errors even though I have a later version of python than required. bittorrent-curses torrentfile.torrent doesn't work either. Help me install a torrent client for my server which uses the command line! Thanks so much!

---

### Post by nitro_n2o on 2007-08-23
The command line torrent is already shipped in with ubuntu installation type this in the terminal 
```
btdownloadcurses.bittorrent <file.torrent>
```
you can also 
btdownloadgui 
btdownloadheadless
btdownloadmany

---

### Post by kavon89 on 2007-08-23
Here are the problems I get. :(

```
kavon@ubuntu-server:~$ btdownloadcurses.bittorrent sf_7.torrent
The program 'btdownloadcurses.bittorrent' is currently not installed.  You can install it by typing:
sudo apt-get install bittorrent
bash: btdownloadcurses.bittorrent: command not found
kavon@ubuntu-server:~$ sudo apt-get install bittorrent
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
bittorrent is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bittorrent: Depends: python-wxgtk2.6 but it is not going to be installed
              Depends: python-twisted (>= 2.0) but it is not going to be installed
              Depends: python-crypto (>= 2.0) but it is not going to be installed
              Depends: python-psyco but it is not going to be installed
              Depends: python-zopeinterface but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kavon@ubuntu-server:~$ btdownloadcurses.bittorrent sf_7.torrent
The program 'btdownloadcurses.bittorrent' is currently not installed.  You can install it by typing:
sudo apt-get install bittorrent
bash: btdownloadcurses.bittorrent: command not found
kavon@ubuntu-server:~$ bittorrent sf_7.torrent
bash: /usr/bin/bittorrent: /usr/bin/python2.4: bad interpreter: No such file or directory
kavon@ubuntu-server:~$
```

I have ' sf_7.torrent ' in my ~ folder.

---

