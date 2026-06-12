---
title: "after sudo make install?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-08
I have installed LiVES and got through the **./configure** then **make** and **sudo make install**, but it is still in that directory waiting for an input, so what do I do now to finish it?

Russty.

---

### Post by bodhi.zazen on 2006-09-08
If make install finished without errors you are god to go.

Try typing lives at the CLI.

If that does not work, look over the output of make install to see where the program was installed.

---

### Post by Russty of Oz on 2006-09-08
YES! it works!!  :biggrin: 

I wasn't sure if I had to do anything else first. 

Thanks for that! :D 

Russty.

---

### Post by 3rdalbum on 2006-09-08
Now that you know how to compile software, I'll give you a little tip.

Download the Checkinstall package (sudo apt-get install checkinstall).

Now in future, instead of doing "sudo make install", do "sudo checkinstall". Follow the prompts (the defaults are usually fine), and Checkinstall will create a Debian package of the program and install it. This way, you can remove it or reinstall it using Synaptic!

Congratulations for completing your first compilation. You're on your way to becoming a full-fledged member of the Linux club :-)

---

### Post by Russty of Oz on 2006-09-08
Thanks for that tip 3rdalbum, I did what you said.

This is getting easier all the time! :D 

Russty.

---

