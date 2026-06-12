---
title: "Aborted jahshaka compile + help removing installed files"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-02
Hi ubuntu community

I need a little help backtracking a little mess I have recently made.

I was attempting to install [jahshaka]("http://www.jahshaka.org") by compiling a tar ball downloaded from sourceforge.

I used the nautilus command in order to move the tar ball to /opt and then untarred the files into /opt.

Having then attempting a ./configure , make; terminal complained about permissions (I did sudo!) and bailed install.

Further to this I installed some dependencies as instructed [here]("http://knecht.homelinux.net/phpBB2/viewtopic.php?t=380&start=0&postdays=0&postorder=asc&highlight=") using ```
apt-get install qt3-dev-tools-embedded qt3-dev-tools-compat qt3-dev-tools libqt3-mt-dev freeglut3 freeglut3-dev
```

I have given up on compiling, and want to remove these files....how can I possibily find and manually remove all of them.....any tips or tricks?

I also added an extra repository in order to download the jahshaka deb, but theres no sign of it in synaptic or by using apt-get :( 

any help will be appreciated!

---

### Post by justin whitaker on 2007-04-02
You can try to remove them via aptitude. You can also use "apt-get remove" all of the apps you listed, just switch remove for install and copy it into a terminal.

---

### Post by TURNER on 2007-04-03
Hi,

Many thanks for your response, I will certainly give it a whirl. :) 

Thanks

Dale

---

