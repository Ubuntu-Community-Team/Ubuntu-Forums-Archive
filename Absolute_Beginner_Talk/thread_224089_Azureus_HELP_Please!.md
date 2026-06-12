---
title: "Azureus HELP Please!"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-07-27
I just got azureus installed and it is sayign it need a required file.  So it downloads it then says "The location '/opt/azureus' isn't writable, this update will probably fail. Check permissions and rety the update." How do I fix this?

---

### Post by shanepardue on 2006-07-27
sheesh..azureus gives me problems too...

did you install this with synaptic? i know that will cause problems.

my azureus works, but i get error messages all day that can't be hidden. i have to click help>about azureus and leave that open to click the hide button for the error messages.

the hassle can be pretty annoying, but azureus is still my bitorrent client of choice.

---

### Post by easyease on 2006-07-27
you need to start it in a terminal as root to install plug ins and do updates.....
 sudo /opt/azureus
then make sure the plug ins are available to "all users" when it asks....

---

### Post by cac007 on 2006-07-27
tried it. it says command not found

---

### Post by easyease on 2006-07-27
sorry my mistake, its
  sudo /opt/azureus/azureus          (that should hit the start up file called azureus in the azureus folder)


also this may be usefull in future.......
"How to open files as root user via right click

    * Read #General Notes 

gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root

    * Insert the following lines into the new file 

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done

    * Save the edited file 

chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root


Right click on file -> Scripts -> Open as root"

follow those instuctions then you will be able to right click on the install icon in the azureus folder and run it as root.

---

### Post by shanepardue on 2006-07-27
if you type "whereis azureus" in the terminal, it will show you exactly where azureus is located on your system. 

then go ahead with the "sudo <location of azureus>" that will open azureus from the terminal as root.

---

### Post by easyease on 2006-07-27
ah cheers mate, i installed azureus myself this afternoon and had same prob as you. i just checked back in my terminal history to see which command sorted it.
 i didnt know about the "whereis" command though and i been using ubuntu fou 18 months so learn something new every day. lol. thanks!

---

### Post by easyease on 2006-07-27
is it working now cac007?

---

### Post by cac007 on 2006-07-27
I don't understand you saw what command sorted it?? what do you mean

---

### Post by richardward101 on 2006-07-27
Personally I recommend doing a manual install from the azureus site into your home folder, then find the beta .jar file from [http://azureus.sourceforge.net/index_CVS.php]("http://azureus.sourceforge.net/index_CVS.php").
This will enable the updates to work properly and will also fix the problem where error messages don't disappear.

---

### Post by Zelut on 2006-07-27
You might want to checkout torrentflux.  It's a web-based torrent client.  I dropped Azureus a while ago due to its memory-whore nature.  TorrentFlux is nice because it can handle multiple torrents, has web-access for remote management, can limit up/down speeds as well as share ratio caps.  It can import torrents via file or remote URL, or even search major torrent sites directly from the interface..

worth a look anyway.. [http://torrentflux.com/](http://torrentflux.com/)

---

### Post by easyease on 2006-07-27
> **cac007 said:**
> I don't understand you saw what command sorted it?? what do you mean
i used the up arrow on my keyboard to go back through my command-line history in terminal to find the one that you need.....
 sudo /opt/azureus/azureus

---

