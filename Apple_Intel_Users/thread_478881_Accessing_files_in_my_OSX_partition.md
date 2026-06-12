---
title: "Accessing files in my OSX partition"
date: 2007-06-19
forum: Apple Intel Users
---

### Post by NickFury on 2007-06-19
Hello everyone,

Been cruising quite nicely with Feisty on my C2D Macbook Pro :)   Thanks for all the great info and help thus far :D

The question I have is concerning the access of my files in OSX.  I can mount my OSX partition fine, and I can even browse a little of it.  When I try to get into say, the 'documents' folder, or 'music' folder in my /home dir in OSX, i will receive a permissions error.  I obviously know the issue has to do with permissions of the folder, and since the OSX partition is basically a '*nix" based Filesystem, ubuntu will adhere to the permission policy for that folder.

Now my main question, is there a way to access these files?  I'm not too concerned about other users being able my documents file in OSX, since I'm the only one who uses this laptop, so.... I know this may be more of an OSX question, but how should I set my permissions up in OSX to access these folders while in Ubuntu?  Sorry, I'm not much a *Nix guru when it comes to permissions, I would hate to screw with the permissions to much in OSX and screw something up there.

Thanks

---

### Post by Greywhind on 2007-06-20
This one's actually not that hard, fortunately. I had the same problem.

Go to "Get Info" on the folders you want to fix permissions on. Show the details on Permissions. Change the drop-down menu under "Others" to either "Read Only" or "Read & Write", then hit "Apply to Enclosed Items". Then close the "Get Info" menu.

---

