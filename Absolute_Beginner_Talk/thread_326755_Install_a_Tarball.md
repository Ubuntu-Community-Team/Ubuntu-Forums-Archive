---
title: "Install a Tarball"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-28
Could someone please tell me how to install this package:  gnome-vfs2_2.16.1.orig.tar.gz.
I unpacked it and ran a patch on one of the files.  When I give the 'configure' command I get the following after a lot of other ouput:

> checking for MODULES_XML... configure: error: Package requirements (glib-2.0 >= 2.9.3 gmodule-no-export-2.0 >= 2.9.3 gthread-2.0 >= 2.9.3 libxml-2.0 >= 2.6.0) were not met:

No package 'glib-2.0' found
No package 'gmodule-no-export-2.0' found
No package 'gthread-2.0' found
No package 'libxml-2.0' found
I can't find any of these packages.  I'd appreciate some help.

Thanks,
Buck

---

### Post by Perfect Storm on 2006-12-28
Why don't you use the one in the repo of gnomevfs2?

---

### Post by Buck2348 on 2006-12-28
> **Artificial Intelligence said:**
> Why don't you use the one in the repo of gnomevfs2?Not sure exactly what you mean.  I downloaded the package I mentioned from the repos, but I don't find a gnomevfs2 in the synaptic list.  I have all the repos enabled as far as I know.  But I don't want to install with synaptic or apt-get because I have a patch for the package.

---

### Post by Perfect Storm on 2006-12-28
It should be in the repo, make sure your repo is set up correctly: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) here's a good place to do so.

The problem with the tarball you downloaded it doesn't "fit" to dapper without compiling 100's of libs and apps as v2.16 of Gnome vfs is to the next generation (edgy ubuntu). You'll run into a heck of a dependency problem.

---

### Post by Buck2348 on 2006-12-28
Thanks very much for your help.  I should have said I'm running Edgy.  I finally got the right package to take care of those dependencies and compiled and installed the gnomevfs.  Unfortunately it didn't fix the problem, which is difficulty with browsing samba shares.  Could you tell me what is the purpose of the second and third files in this list which were offered for download?  Are they compilable and/or installable?  I have no idea what to do with them.
   >  * gnome-vfs2_2.16.1.orig.tar.gz (2.7 MiB)
    * gnome-vfs2_2.16.1-0ubuntu4.diff.gz (23.0 KiB)
    * gnome-vfs2_2.16.1-0ubuntu4.dsc (1.8 KiB)
Thanks again.

Buck

---

### Post by malegria on 2006-12-28
I suggest you update your repositories list as found here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software)

Once you follow those instructions open a terminal and type in:
```
sudo apt-get install libgnomevfs2-0 
```

That should get you going.

---

### Post by deadgobby on 2006-12-28
Here is a couple of very use full links
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Gobby

---

### Post by Buck2348 on 2006-12-29
> **malegria said:**
> I suggest you update your repositories list as found here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software)

Once you follow those instructions open a terminal and type in:
```
sudo apt-get install libgnomevfs2-0 
```

That should get you going.I did update the repo list and a check with synaptic shows I have the latest version of libgnomevfs2-0.  I would just like to know in general what those files with the .dsc and .diff.gz are for.  Are they used somehow when compiling and installing a source package?
> Here is a couple of very use full links
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Gobby
Thanks, those are useful.

Thanks for the replies,
Buck

---

### Post by Frak on 2006-12-29
> **Buck2348 said:**
> I did update the repo list and a check with synaptic shows I have the latest version of libgnomevfs2-0.  I would just like to know in general what those files with the .dsc and .diff.gz are for.  Are they used somehow when compiling and installing a source package?

Thanks for the replies,
Buck
all I can say is that .gz is a archive zip.

---

