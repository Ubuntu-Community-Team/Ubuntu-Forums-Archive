---
title: "problem unpacking .deb files"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by knassy on 2006-02-15
Hey I've tried installing automatix and also the w32codecs but when it comes to unpack the .deb files terminal gets as far as displaying 'Setting up Automatix...' or 'Setting up w32codecs' then stops. Seeing it happens to both im assuming its a problem with me unpacking the deb files rather than anything else. ANy advice what this might be? Thanks

---

### Post by carlosqueso on 2006-02-15
are you unpacking them with sudo dpkg -i ?  If you are and it doesn't give you an error message, then there may be a problem with your install.  Also, do apt-get or synaptic work?

---

### Post by fer5437 on 2006-02-15
Here the step by step how to install Automatix

```

 How to get Automatix

    * Read #General Notes
    * Read #How to add extra repositories 

    * To install Automatix in Ubuntu 

sudo apt-get install xterm
wget http://beerorkid.com/automatix/automatix_5.4-2_i386.deb
sudo dpkg -i automatix_5.4-2_i386.deb

    Applications -> System Tools -> Automatix 

    * To install Automatix in Kubuntu/Xubuntu 

sudo apt-get remove automatix-kubuntu
sudo apt-get install xterm libglade2-0 libgnomecanvas2-0
wget http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
sudo dpkg -i zenity_2.10.0-0ubuntu1_i386.deb
wget http://beerorkid.com/automatix/automatix_5.4-2_i386.deb
sudo dpkg -i automatix_5.4-2_i386.deb

    Main Menu -> System -> Automatix 

```

Hope this can help...:p

---

