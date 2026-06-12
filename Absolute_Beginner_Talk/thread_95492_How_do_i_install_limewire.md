---
title: "How do i install limewire?"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by softwarepirate on 2005-11-26
how do i install limewire?:confused:

---

### Post by NewAgePirate on 2005-11-26
go to your terminal and type:

[I]wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh[/I]

then Insert the following lines into the new file:

[I]cd /opt/LimeWire/
./runLime.sh[/I]

Now go back to Terminal and type:
[I]sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop
[/I]

Then when gedit comes up type this:
[I][Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;[/I]

Then save and exit all those and look under "internet" on the main ubuntu menu. You should see a Limewire icon.


~Chloe

---

### Post by NewAgePirate on 2005-11-26
> **NewAgePirate]go to your terminal and type:

[I]wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh[/I]

then Insert the following lines into the new file:

[I]cd /opt/LimeWire/
./runLime.sh[/I]

Now go back to Terminal and type:
[I]sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop
[/I]

Then when gedit comes up type this:
[I][Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application said:**
> 

Then save and exit all those and look under "internet" on the main ubuntu menu. You should see a Limewire icon.


~Chloe


Hmm. Now that I try it myself, that didn't quite work. All I have is the icon for it and the program doesn't launch. Did it work for anyone else?

~Chloe

---

### Post by softwarepirate on 2005-11-26
hmm.. Cannot launch entry

Details: Failed to execute child process "runLime.sh" (No such file or directory) :(

---

### Post by NewAgePirate on 2005-11-26
[QUOTE=softwarepirate]hmm.. Cannot launch entry

Details: Failed to execute child process "runLime.sh" (No such file or directory) :([/QUOTE]

Well, I'm quite new at this myself, but I guess we could play around with it until somebody qualified comes along :)

I found that LimeWire.zip had been placed into my home folder, so maybe if you go there and unzip it (right-click and select "extract here") it would work better. 

From there I entered the folder and found *runLimeWire.sh* and dragged it into a terminal so it would execute. The only error I got was about not having JRE, so that might be a good start.
Maybe you have JRE, or if not they have if at [www.java.com](www.java.com)

~Chloe

---

### Post by Vorian on 2005-11-26
You need to install java for it to work.

you can use synaptic to install it...

---

