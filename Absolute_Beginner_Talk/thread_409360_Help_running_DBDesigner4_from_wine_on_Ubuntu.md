---
title: "Help running DBDesigner4 from wine on Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by j1n3l0 on 2007-04-14
Hi,

I've just installed wine and DBDesigner4 on my Ubuntu 6.10. I then followed some [instructions]("http://21croissants.blogspot.com/feeds/3550112704730532833/comments/default") to fix a bug (notifications opened in the background) which stated:

```
sudo apt-get install devilspie
echo ‘[if[contains [application_name] "DBDesigner"] [focus]]’ > $HOME/.devilspie/dbdesigner.ds
devilspie
```

Step 1 is fine but when I do step 2 I get the following error:
```
bash: /home/nelo/.devilspie/dbdesigner.ds: No such file or directory
```

I can't find the **.devilspie** directory anywhere! But the application was installed and I'm working in my home directory :( What am I missing here? Sorry folks ... I'm not very adept at bash scripting :(

Your help is much appreciated! Thanks in advance!

Nelo

---

### Post by Stickymaddness on 2007-04-16
Try using synaptic to install it, else try [http://www.fabforce.net/downloadfile.php?iddownloadfile=2]("http://www.fabforce.net/downloadfile.php?iddownloadfile=2")

---

### Post by j1n3l0 on 2007-04-16
Cheers for that! Got a solution for it.

The file I was looking for was in the .wine directory. I had to create the .devilspie directory and copy the dbdesigner.ds file over and then run the command in step 2 again.

At the moment it works though I'm not entirely sure I did it right. Will have to cross check when I install Ubuntu 7.04!

Thanks

Nelo

---

