---
title: "Installing Medusa4 Personal"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by drmbogo on 2007-04-17
Hi Folks!
Downloaded and extracted the Medusa tarball which leaves me w/ 2 pdf files, a .jar file, and "medusa4_pers_linux"
When I click on the medusa file, a dialog opens asking how I would like to open the file, "run", Run in Terminal", or "Display"
Now when I try to run it or run in a terminal, the installer starts and tells me to log in as administrator to proceed.
I'm not really sure how to do this, and I don't know how to run this from a command line.
I do know how to use sudo, but somehow I've missed the syntax to run this installer...

Sorry for the noob Q!
Thanks in advance!
Dave

---

### Post by Seisen on 2007-04-17
Try this in the terminal 
```
sudo java -cp filename.jar
```

---

### Post by drmbogo on 2007-04-17
Ok, tried that. no luck.
here's what returned:
dave@dave-desktop:~/Desktop/medusa/medusa4_210_personal_linux$ sudo java -cp medusa4pers.jar
Password:
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

Just for giggles I tried:
dave@dave-desktop:~/Desktop/medusa/medusa4_210_personal_linux$ sudo gij -jar medusa4pers.jar -cp
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp001/2737645
WARNING: could not delete temporary file /tmp/ismp001/9598473

I have to say that, while frustrating, I am learning a lot on the command line! The problem of course, is retention!

I hadn't thought of trying to access the jar directly. There must be something in the executable text file that won't let me, tho'.

Thanks, Seisen, for your reply
Any other ideas?

---

### Post by drmbogo on 2007-04-18
SOLVED

Here's how I did it:
In a terminal:
```
sudo -i
```

This sets me as root user.
Then navigate to folder containing the medusa installer and .jar (I'm assuming these need to be in the same directory)
Then:
```
./medusa4_pers_linux
```

That's pretty much it. I just followed the prompts from there...

Hope this helps somebody!
Cheers

---

### Post by MichaelSM on 2007-08-08
Thank you drmbogo. I just got Medusa4 and it's installing right now. I didn't know how to install as root before, so now I should be able to install OpenCascade which had similar issues to Medusa4.
Great.
Mike.:)

---

