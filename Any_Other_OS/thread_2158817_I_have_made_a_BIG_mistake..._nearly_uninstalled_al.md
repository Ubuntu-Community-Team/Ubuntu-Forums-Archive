---
title: "I have made a BIG mistake... nearly uninstalled all my packages. How can I revert?"
date: 2013-06-30
forum: Any Other OS
---

### Post by ABigMistake on 2013-06-30
I'm very much ashamed I made such a big mistake. I've spent the last week or so installing everything I need on my new installation, and now I've gone and ruined it all. I had installed the xorg-edgers PPA, and thought that there was a problem with the installation. So I ran a ppa-purge on the xorg-edgers ppa... it asked me if I was really sure I knew what I was doing, and somehow I missed the entire list of packages it was going to install and went with it. Now I basically uninstalled all my applications. So can someone forgive my poor blunder, and possibly let me know what options I have? I read that there are archives of packages in /var/cache/apt/archives... is there a way to install all of them in that directory? Or is there another way to revert to what I had before? Or is my only option to do a clean install? :( I was running Linux Mint 15, based on Raring, if that means anything. Thanks for the help. (not sure why I'm not allowed to make new paragraphs here...?)

---

### Post by Frogs Hair on 2013-06-30
Moved to Other OS/ Distro Support - Mint 15 

ABigMistake, use the edit button to add any relevant information.

---

### Post by ajgreeny on 2013-06-30
I have done exactly what you did in the past using ubuntu 10.04, so don't worry, you're not totally alone in feeling a real chump; just like I did.

I presume you now have only a command line when you boot, or have you not yet closed the session?  If you still have the GUI session open you can still use the software-centre (or better synaptic, though you may have to install that first) to put matters right.

You can find what was removed by running command ```
grep -iw remove /var/log/dpkg.log.1 && grep -iw remove /var/log/dpkg.log
``` which will list everything removed with a date showing, so you should be able to see what disappeared when you purged the ppa.  It may be only xorg and the variouys xorg packages that are needed for the GUI, and you may not be able to depend on your package cache as I'm afraid that will possibly only contain the ppa versions of xorg packages.

I hope that helps.  Let's see what was removed then we can figure out best how to get them all back

---

### Post by ronniew on 2013-06-30
Reinstall without losing your stuff.

[http://askubuntu.com/questions/291376/how-to-reinstall-ubuntu-13-04-raring-ringtail-safely](http://askubuntu.com/questions/291376/how-to-reinstall-ubuntu-13-04-raring-ringtail-safely)

---

### Post by ABigMistake on 2013-07-01
Thanks for the replies everyone. In my desperation, I ended up formatting and reinstalling everything while everything I did in the past week was still fresh in my mind. It didn't take as long as I expected to start over.

After the fiasco, I ended up restarting the computer, and apparently, I couldn't even get into the filesystem anymore, as the disk was encrypted and the encryption got messed up, too. I believe I got a command line afterwards, but I'm not sure anything would be possible to restore due to the encryption failing. That would probably also render ronniew's answer useless, as well.

Thanks anyhow! You can rest assured knowing I've learned a lesson =)

---

