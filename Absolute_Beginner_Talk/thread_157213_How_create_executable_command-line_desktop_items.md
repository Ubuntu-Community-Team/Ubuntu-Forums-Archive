---
title: "How create executable command-line desktop items"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-04-08
This is CLEARLY  an absolute beginner Linux question.

I have installed LAMPP ([http://www.apachefriends.org/en/xampp.html)](http://www.apachefriends.org/en/xampp.html)).  I have used this in Windows before and like the integrated nature of the project.

In any case, the command to start the package is sudo /opt/lampp/lampp start and the command to stop is sudo /opt/lampp/lampp stop

I want to create two icons on my desktop (KDE), one for starting and one for stopping.

I am able to launch the apps at boot using information here 
[http://www.apachefriends.org/en/faq-xampp-linux.html#fsl](http://www.apachefriends.org/en/faq-xampp-linux.html#fsl)

But I would still like to know how to create an executable file on my desktop that I can use to stop and restart the LAMPP application.

Thanks

---

### Post by incubus on 2006-04-10
How about something like this:

Create a text file 'lampp_start.sh' in your ~/Desktop directory. Copy and paste this:
```

#!/bin/bash
gksudo /opt/lampp/lampp start

```
(If you're using KDE, replace 'gksudo' for 'kdesu'.)

Now create the script 'lampp_stop.sh':
```

#!/bin/bash
gksudo /opt/lampp/lampp stop

```

Finally, make them executable:
```

$ cd ~/Desktop
$ chmod +x lampp_start.sh
$ chmod +x lampp_stop.sh

```

You're gonna ask me how to make it appear in a terminal window, as it does in windows. I confess I don't know. I hope somebody can give a hand there.

incubus

---

