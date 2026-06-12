---
title: "Absolute Beginner wants to use Ubuntu as a server"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by bumcheekcity on 2005-10-23
OK,  so Im an absolute beginner. I managed to acquire a working but painfully slow machine (333Mhz, 128MB RAM, onboard Graphics), to run Ubntu Linux in a more than usable fashion. It's not connected to my network, has a CD-ROM and Floppy drive though. 

I'm thinking of usng this as a server once I get used to it, and connecting it to my network, using 2NIC's, and get it to simply route my connection through the house, and maybe try to get it hostng some PHP/mySQL/Apache webpages. Nothing too fancy.

Major question is: What do I do with it now? I know just about no linux at all, but have had general success trying to just do basic windows-like stuff using the GNOME interface. You now, juut moving files around, opening and savig stuff asnd generally pottering around to get a feel for it.

I havent installed anything yet, asnd note that linus installers seem to be in the format of .tar.gz, and I think i remember reading that you dont install them like Windows stuff, but that you have to do something different, unlike double-clicking an .exe and letting it do the rest.

Anyone give me any help? I'm not stuck on anything, I'm just wondering how best to use my new machine.

---

### Post by Mustard on 2005-10-23
I don't know much about setting up servers myself, but I know that the Ubuntu install CD has a 'server' install option, that installs the minimal files to run a server.  I assume it will install a command line environment and that you may, if you wish, install some type of simple gui interface like xfce or fluxbox if you require a gui.

---

### Post by sophtpaw on 2005-10-23
[QUOTE=bumcheekcity]OK,  so Im an absolute beginner. I managed to acquire a working but painfully slow machine (333Mhz, 128MB RAM, onboard Graphics), to run Ubntu Linux in a more than usable fashion. It's not connected to my network, has a CD-ROM and Floppy drive though. 

I'm thinking of usng this as a server once I get used to it, and connecting it to my network, using 2NIC's, and get it to simply route my connection through the house, and maybe try to get it hostng some PHP/mySQL/Apache webpages. Nothing too fancy.

Major question is: What do I do with it now? I know just about no linux at all, but have had general success trying to just do basic windows-like stuff using the GNOME interface. You now, juut moving files around, opening and savig stuff asnd generally pottering around to get a feel for it.

I havent installed anything yet, asnd note that linus installers seem to be in the format of .tar.gz, and I think i remember reading that you dont install them like Windows stuff, but that you have to do something different, unlike double-clicking an .exe and letting it do the rest.

Anyone give me any help? I'm not stuck on anything, I'm just wondering how best to use my new machine.[/QUOTE]
I don't know about Networking either, but Mustard is along the right lines there. Install with Networking in mind will give you the right foundation. Also, with your spec Gnome is going to be 'heavy' to run. Your system must feel slow and sluggish at the moment. Something like xfce will make all the difference.

Installing should be easy. Mostly you shouldn't need to deal with tar.gz files yourself, although you will sometimes and then it ain't that hard either. But mostly all the packages you want should be in your repositories. check the ubuntuguide.com to max your repositories. Then it is simply a matter of pointing and clicking if you're using Synaptic. For Synaptic go to System/Administration/Synaptic Package Manager. I currently have a total of 17,803 packages available at hand to choose from. Click search and put in something you might want. XFCE for example! it will find it, after which you click on it to select it, and hit 'apply' Synaptic will then download and install it for you taking care of any dependency issues along the way. Couldn't be easier.
I hope that helps a little
--

sophtpaw

P.S

I borrow this from Aysiu: [http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php) walks you through basic installations using Synaptic in a graphical way.
As for xfce when you need to reboot and at your login page choose xfce instead of Gnome, which you can specify to make default or just for that session

---

### Post by David Marrs on 2005-10-23
If you're still at the stage where you just want to learn how to use apache, mySQL and PHP, I'd recommend simply installing them on your system now. It's quite easy to do. Open synaptic from the system administration menu and install apache2, PHP5, mod-php, mySQL and the PHP-mySQL interface (I forget what it's called but you should be able to find it easily enough) and you should (touch wood) have a working system ready to go. It would also be worth your while to install all the doc packages associated with those applications.

Open firefox and enter localhost at the address bar. If you see a placeholder page or a directory listing then you know that apache's working.

Place files you want to serve in /var/www/ and start playing.

You may want to give your user account write access to that directory or (what I do) store your html/php files in your home directory and symbolically link to them from /var/www/. Type 'ln --help' or 'man ln' for more information on how to use links. Typical syntax would be:

sudo ln -s ~/myProject/ myProject

That would create a link called /var/www/myProject which, if you tried to open it, would lead you to /home/username/myProject. If you load localhost/myProject in your browser you should see a directory listing. Alternatively, if you already have a file in myProject called index.html, you'll see that instead.

---

