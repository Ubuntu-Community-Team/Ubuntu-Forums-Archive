---
title: "[SOLVED] How to install screenlet?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-15
I downloaded the file for the Weather screenlet (from [http://www.screenlets.org/index.php/Clear_Weather](http://www.screenlets.org/index.php/Clear_Weather)), but I don't know how to get it to install. I extracted the archive to my desktop, but I don't know what to do from there. The instructions on the download page are not helpful at all.

Thank you!

---

### Post by santiagoward2000 on 2007-11-15
HI!
You have to extract the file and copy the folder to /home/yourusername/.Screenlets
If the folder doesn't exist, just create it.

---

### Post by doctorbighands on 2007-11-15
Okay. I created a file in my home folder called ".Screenlets" and moved the extracted file from my desktop to the new folder.

Now what?

---

### Post by santiagoward2000 on 2007-11-15
> **doctorbighands said:**
> Okay. I created a file in my home folder called ".Screenlets" and moved the extracted file from my desktop to the new folder.

Now what?

Oh, wait. Have you installed Screenlets first?
If not, you can find the instructions here:
[http://screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users]("http://screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")

Then, open screenlets-manager and run the screenlet you want.

---

### Post by doctorbighands on 2007-11-15
I opened the screenlets manager, but when I hit "install," it can't find the folder called ".Screenlets". Does the period make the folder hidden? If so, why does it need to be hidden?

---

### Post by Paul820 on 2007-11-15
Make a folder inside your home folder called **.screenlets**, lowercase s. Now that folder what you extracted, put that inside the .screenlets folder that you made. Start the screenlets manager and the screenlet will appear with all the others. Double click your screenlet and it will start. Simple :)

---

### Post by doctorbighands on 2007-11-15
> **Paul820 said:**
> Make a folder inside your home folder called **.screenlets**, lowercase s. Now that folder what you extracted, put that inside the .screenlets folder that you made. Start the screenlets manager and the screenlet will appear with all the others. Double click your screenlet and it will start. Simple :)



THANK YOU!!

I was getting very disenchanted with the whole thing! I'm glad it finally works.

---

### Post by Paul820 on 2007-11-15
No problem :) Enjoy your screenlets, there are some very good ones on the screenlets homepage.

---

### Post by antisocialist on 2007-12-11
wow this is helpful, and easy to follow, check this screenlet out on gnome-look

[http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172)

---

### Post by wsonar on 2007-12-19
HOW DO I MAKE THEM QUIT STARTING......

I have unchecked them from starting
I have removed screenlets from my sessions
I have saved my sessions to remember running apps without them running
I have rm the directory

none the less they all load every time I login I got smooth weather, clear weather, and the clock all starting and have to kill them all I decided to just use the weather with AWN

also is there a setting in the AWN time to change it from black text to white if you have a black background you can't see the time?

---

### Post by jryprt on 2007-12-19
> **wsonar said:**
> HOW DO I MAKE THEM QUIT STARTING......

I have unchecked them from starting
I have removed screenlets from my sessions
I have saved my sessions to remember running apps without them running
I have rm the directory

none the less they all load every time I login I got smooth weather, clear weather, and the clock all starting and have to kill them all I decided to just use the weather with AWN

also is there a setting in the AWN time to change it from black text to white if you have a black background you can't see the time?

Open home folder press Ctrl+h look for  .config open it go to Screenlets
open it delete any or all in there .

---

### Post by brunods on 2008-01-16
check you /home/username/.config/autostart folder
Probably there are some autostarts there!
Get 'em out of there if you want them off

---

