---
title: "My Outstanding Issues"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2005-12-06
1. GL Screensavers do not work after reinstalling Open Office org
2. Mounting a network share so that its available as part of the file system
3. Wine - support for OLE - Frontpage open/import web issue
4. Evolution - Delete mail after x days on server.
5. Scanner - visioneer 6200 USB scanner not detected

Any help? I've listed them by priority. Hope someone has some valuable insight.

---

### Post by Joe_CoT on 2005-12-06
> 2. Mounting a network share so that its available as part of the file system

[How to mount network folders on boot-up](http://ubuntuguide.org/#automountnetworkfolders). That's one O:-)

as for the first one, *shrug*, try reinstalling xscreensaver?

---

### Post by Stormspace on 2005-12-07
Reinstalling xscreensaver doesn't fix the glscreensavers, neither does running automatix which is supposed to put the non-free nv drivers on.

As for the network mount. I'm getting a wrong file system type on the line

//tivoserver/music /media/music  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

I also tried the ip instead of the computername with the same result.

I entered per the instructions for a read/write connection. I tried vfat as well and it didn't work either.

Ideas?

---

### Post by YokoZar on 2005-12-08
[QUOTE=Stormspace]3. Wine - support for OLE - Frontpage open/import web issue

Any help? I've listed them by priority. Hope someone has some valuable insight.[/QUOTE]
Try using the latest Wine from the Winehq APT repository: [http://www.winehq.org/](http://www.winehq.org/)  (click downloads, then Ubuntu)

---

### Post by Joe_CoT on 2005-12-08
> As for the network mount. I'm getting a wrong file system type on the line

are you sure you have samba and smbfs installed? that's the error i got when i hadn't installed smbfs

---

### Post by Jengu on 2005-12-08
[QUOTE=Stormspace]1. GL Screensavers do not work after reinstalling Open Office org[/quote]

Be more specific. Do you get an error? Do they just show up as black? Do other OpenGL applications work? If you don't have any other OpenGL apps, open a console and run "glxgears" without the quotes and report back any errors you get.

> 
3. Wine - support for OLE - Frontpage open/import web issue


What functionality do you need exactly? Rather than trying to use wine, have you looked to see if any native apps, like Nvu, could do the job? Also try the latest build as suggested above.

---

### Post by Stormspace on 2005-12-08
[QUOTE=YokoZar]Try using the latest Wine from the Winehq APT repository: [http://www.winehq.org/](http://www.winehq.org/)  (click downloads, then Ubuntu)[/QUOTE]

I'm fairly certain I'm using the latest, but I will double check. :)

---

### Post by Stormspace on 2005-12-08
[QUOTE=bobfnordman]are you sure you have samba and smbfs installed? that's the error i got when i hadn't installed smbfs[/QUOTE]

Again, I am fairly certain it's installed. I can browse other computers on the network and see the share contents. I thought samba was needed to do that. I can check the packages in synaptic to see if smb is installed tho.

---

### Post by Stormspace on 2005-12-08
[QUOTE=Jengu]Be more specific. Do you get an error? Do they just show up as black? Do other OpenGL applications work? If you don't have any other OpenGL apps, open a console and run "glxgears" without the quotes and report back any errors you get.
[/quote]

The screen saver tries to load the preview and then displays a message to the effect that the preview can't display. This started immediately after uninstalling OOo.1 (or whichever one comes with the distro) I uninstalled it and reinstalled OOo.2. (I did this because none of the OO apps would load.) 

[QUOTE=Jengu]
What functionality do you need exactly? Rather than trying to use wine, have you looked to see if any native apps, like Nvu, could do the job? Also try the latest build as suggested above.[/QUOTE]

Frontpage opens fine and though I haven't tested every aspect I cannot open a web thats located on the web. I typically work with my hobby site live so that I can maintain it from multiple locations. As for native apps, I am too deeply entrenched to migrate away from FP at this time.

---

### Post by Stormspace on 2005-12-12
> 2. Mounting a network share so that its available as part of the file system

I used the method described above, however I was using a account other than the admin account. Once I changed the credentials to the administrator account on the windows 2000 box, the file share mounted.

Another one down...though another issue has popped up. More in another thread.

---

### Post by Stormspace on 2005-12-12
> 1. GL Screensavers do not work after reinstalling Open Office org

3. Wine - support for OLE - Frontpage open/import web issue
4. Evolution - Delete mail after x days on server.
5. Scanner - visioneer 6200 USB scanner not detected

Wine is the current version, installed from the repository on the winehq site.

---

