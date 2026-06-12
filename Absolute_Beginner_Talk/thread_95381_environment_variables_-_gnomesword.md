---
title: "environment variables - gnomesword"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by steviecee on 2005-11-26
I have been given some gnome sword modules on a cdrom.

I have configured gnomesword to the so the it can see the modules on the cd and selected install but this does nothing.

I am told I need to copy the modules to my Hard Drive and set an environment variable.  How do I do this - step by step please?

---

### Post by matthew on 2005-11-26
I seem to recall reading something on the Sword Project web site at [http://www.crosswire.org/sword/index.jsp]("http://www.crosswire.org/sword/index.jsp") on how to install modules. Let me see if I can find it.
 
 Here it is:[LIST]
[*]**Raw**: Find the directory where your sword modules are installed. This directory will contain subdirectories: mods.d and modules. Some possibilities include \Program Files\CrossWire\The SWORD Project, or /usr/share/sword. Unzip the module to this directory. The module zip file will unzip to populate the mods.d and modules subdirectories.[/LIST]From this page: [http://www.crosswire.org/sword/modul...uleinstall.jsp]("http://www.crosswire.org/sword/modules/moduleinstall.jsp")
 
So, look on your computer for the location of the current modules. /usr/share/sword seems the most likely place and is where they are installed on my computer.
 
Here is how you transfer the files you have to that directory. I will assume they ae currently in /media/cdrom. Do this for each module you downloaded. Make sure GnomeSword is closed while you are doing this.
 
 Open a terminal from Applications->Accessories->Terminal and type
      Code:
     [LEFT]sudo mv /media/cdrom/modulename /usr/share/sword/modulename
[/LEFT]
   
  
That may do it--I don't know if the modules on your cdrom are in zip format and need to be uncompressed or if they are already uncompressed and will need to be put into the proper directories in /usr/share/sword/modules. I recommend you use Nautilus (the default graphic filebrowser in Ubuntu) to look at /usr/share/sword first and explore it a bit to see where your files need to go. 

Once the files are in the right place, all you have to do is open GnomeSword and they should be there. I don't know anything about needing to set an environment variable. I never needed to do anything like that. It would probably be a good idea to take a look at the Sword Project web pages I referenced at the top of this post for a while before you do anything...there might be an even better method for you there.

See also: [http://ubuntuforums.org/showthread.php?t=10697]("http://ubuntuforums.org/showthread.php?t=10697")

---

