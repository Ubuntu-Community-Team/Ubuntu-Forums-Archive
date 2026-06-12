---
title: "Thunderbird Importing from windows"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-12
Hello there! I'm trying to import my mails from my windows partions but mozilla only displays the folders, no messages at all.

Here's what've done:

1st moved everthing from the <user-dir>/.mozilla-thunderbird into a old directory

2nd copied the entired <windows mount>/documents and settings/<user>/application data/Thunderbird to the above dir

3rd changed the permissions to 755 of the registry.dat, profiles.ini and the Profiles dir (using recursive option)

But all i get is the folders name, can't see my mails.

Any ideas?

---

### Post by u.b.u.n.t.u on 2006-06-12
1. Places > Home Folder

2. View > Show Hidden Files

3. Find and open the directory ".mozilla-thunderbird"

4. Double click "profiles.ini" (you want this open in a text editor such as gedit).

5. Change the path, using this example as a guide, so that it leads to your Thunderbird profile:

"[General]
StartWithLastProfile=1

[Profile0]
Name=XYZ on XYZ-desktop
IsRelative=0
Path=/media/storage/My System Files/XYZ thunderbird/profile.default
Default=1"

Note: My path is on a separate HDD. You want the path to point to your Thunderbird profile. This has the added benefit of easily backing up your profile.

---

### Post by viniciuscarvalho on 2006-06-16
[QUOTE=u.b.u.n.t.u]1. Places > Home Folder

2. View > Show Hidden Files

3. Find and open the directory ".mozilla-thunderbird"

4. Double click "profiles.ini" (you want this open in a text editor such as gedit).

5. Change the path, using this example as a guide, so that it leads to your Thunderbird profile:

"[General]
StartWithLastProfile=1

[Profile0]
Name=XYZ on XYZ-desktop
IsRelative=0
Path=/media/storage/My System Files/XYZ thunderbird/profile.default
Default=1"

Note: My path is on a separate HDD. You want the path to point to your Thunderbird profile. This has the added benefit of easily backing up your profile.[/QUOTE]


sorry took too long to test, that didn't work. When I edit the path, it was:

Path=Profiles/default/ksdjalp0.slt
so I tried: Path=/home/vinicius/.mozilla-thunderbird/Profiles/default/ksdjalp0.slt

Thunderbird does not even start...
It says that it is already running...

Any other suggestions?

Regards

---

### Post by XPerienced on 2006-06-17
I'm also having problems with this. 

I will follow this thread and answer you if I find a solution.

XPerienced

---

