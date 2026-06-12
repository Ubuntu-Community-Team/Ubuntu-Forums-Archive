---
title: "Installing flash"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by diarmuid on 2006-07-09
Hiya,
I reccently installed ubuntu, and have been trying to install flash player.  I downloaded the install archive from the web, but have been unable to run the installer file.  THe documentation says I need to run it from 'command line' but I don't know what that is/how to access it.  The only other documentation I could find, suggested moving the nessecary files to the firefox folder, but I am unable to as I don't have permission.  So does anyone know how to change the permission, or install using command line?

Thanks

Diarmuid

---

### Post by Kobalt on 2006-07-09
Hi,

To install your flash player, first extract the archive you downloaded in your home folder. Then, go to Applications > Accessories > Terminal (or Console). Then, type these command lines : 
```
cd /home/"yourhomefoldername/install_flash_player_7_linux/"
```
```
./flashplayer-installer
```
Answer the questions you are asked, and you're done ! 

Cheers !

---

### Post by aeto on 2006-07-09
ok. therez another way. u dont need to download off macromedia. just go to applications > accessories > terminal

in the terminal, type the following:

sudo apt-get install flashplugin-nonfree

---

### Post by parkash on 2006-07-09
Don't struggle so much...

There's one solution:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There's another:

```

$sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

```

Then replace the content of sources.list with the sources found in:
[HTML]
http://italy.copybase.ch/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/
[/HTML]

Follow the instructions at the end of the page to solve the gpg key problems.

And finally, install flash with Synaptic.

I hope that helps and I hope too that I was clear enough :rolleyes:

---

### Post by FrancoNero on 2006-07-09
> **Kobalt said:**
> Hi,

To install your flash player, first extract the archive you downloaded in your home folder. Then, go to Applications > Accessories > Terminal (or Console). Then, type these command lines : 
```
cd /home/"yourhomefoldername/install_flash_player_7_linux/"
```
```
./flashplayer-installer
```
Answer the questions you are asked, and you're done ! 

Cheers !

but 7 is not the latest version, so you'll be locked out of many websites

---

### Post by shoot2kill on 2006-07-09
like AETO said, use the following code in terminal...

> sudo aptitude update
sudo aptitude install flashplugin-nonfree

---

### Post by diarmuid on 2006-07-09
Hiya,

I have tried all of the above, however I have been unable to get any of them to work.
Kobalt: I tried your suggestion, but whether I was typing it wrong, or something else, the terminal, said it was unable to find the folder/file.

Parkash and Aeto: I tried both of the 'sudo' commands you suggested however the terminal said that I needed a password, and wouldnt let me type the password in.

Thanks for all of your help so far

P.S.
I don't know whether it makes a difference, but I am running the AMD64 bit version of ubuntu.

---

### Post by cyberlite on 2006-07-09
I know that problam just type the password and hit enter and vuala.
You just can,t see what you writing and the curser will not move.

---

### Post by Kobalt on 2006-07-09
> **diarmuid said:**
> P.S.
I don't know whether it makes a difference, but I am running the AMD64 bit version of ubuntu.
Yes, it makes all the difference... There isn't a flash player yet for AMD64... What I did to install flash on a 64bit machine was to install a 32bit version of Firefox and it's plugin for flash. 
To do so, Open a command line and type this : 
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
``` (type your pasword when you're asked to, it's normal not to see the cursor move, then hit enter and you're done)
then download firefox 32bit in your home folder : [URL="http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US"]
http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US[/URL]
Then, you got to the fiorefox directory in command line : 
```
cd ~/home/yourhomefolder/firefox/
```
Make a repertory for firefox :
```
mkdir /usr/local/firefox32
```
```
cp -r -p ./* /usr/local/firefox32/
```
You create the exec : 
```
sudo gedit /etc/pango32/pangorc
```
Paste these lines in the blank file you get, then close it and save it. 
> [Pango]
ModuleFiles=/etc/pango32/pango.modules'&#8217;
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
Create another file, 
```
sudo gedit /usr/local/bin/firefox32
```
Paste the following lines, close & save 
> #!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /usr/local/firefox32/firefox $@
And finally, make the launcher work with : 
```
sudo chmod +x /usr/local/bin/firefox32
```

And you're done ! Now you can install flash with one of the ways you have been given here, and hope it works.

Cheers !

---

