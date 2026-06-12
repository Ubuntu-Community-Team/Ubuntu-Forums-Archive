---
title: "Installing and running commercial windows app using wine"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by shashman on 2007-02-27
Hi there - newbie alert!

I've been working with edgy desktop for a while now and have managed to get pretty much everything I need set up right, however in my business I use a third party application called "tele-connect" running on windows (nt/2000/xp) and I'd like to try to get this to run on ubuntu. If I can, this opens the door to a complete replacement of Windows across the business.

Using a virtual pc based solution isn't really an option as the hardware we're using would need some upgrading to make this a viable solution...

I've read the wine guide at the winehq, but I have a question that some of you might help with?

My windows app requires installing to operate in windows. This process involves (obviously) copying some files to the local machine, and making some entries in the registry. Am I right in thinking that this process can't be run in the same way under wine and that I will have to identify the files that are copied and the registry changes that are made in windows, then replicate these changes on my ubuntu installation and in my wine configuration files?

Any help would be gratefully received.

---

### Post by v8YKxgHe on 2007-02-27
If you install Wine via Synaptic (System->Admin->Syanptic) or by typing in terminal:

```
sudo apt-get install wine
``` 

Which ever you prefer. You should then just be able to double click on the .exe file and it will install as normal.

---

### Post by cendant on 2007-02-27
If the above method does not work for you, try to copy your EXE file to the hidden folder ~/.wine/drive_c and in terminal type this

wine "c:\PROGRAM_NAME.exe"

---

### Post by Patrick K on 2007-02-27
Wine has a registry and a place for dll's. It will take care of these details automatically. Installing is just like in windows. Let it install in the default Program Files directory.

If this is a very complex app, it is possible it won't run in wine. All you can do is try it. There is a link at winehq to check it's database of what apps work. It is user supported so unless someone else has tried it, there is no way to know in advance if it will work. 

The app install method I use is to fire up winefilw, its file manager, and run the install exe from it. 

Good luck!

---

### Post by shashman on 2007-02-27
Thanks all. Very helpful. I've followed your suggestions and all has gone well except that I'm hitting a fairly non-descript error during one phase of the installation.

"an error occurred during the move data process: -199"

"Component: Runtime Client\System Windows"
"File Group: Windows System Registered"
"File: c:\windows\system32\grid32.ocx"

this happens during the copying files stage of the installation and the install aborts without completing.

Any thoughts on a possible cause, fix or workaround?

---

