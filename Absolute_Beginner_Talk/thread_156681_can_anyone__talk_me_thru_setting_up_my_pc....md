---
title: "can anyone  talk me thru setting up my pc..."
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by lesada411 on 2006-04-07
to get videos to play on the totem player?  Do I have to download something so that i can play them?  If so what is it and where can i find it.   Thank-you

---

### Post by bscbrit on 2006-04-07
You are probably missing the w32codecs, which will allow totem, xine and others to play all the video formats commonly used under windows.  You will have to install it using synaptic.  I can't recall which repos it is in, but a quick search on google gave me this link:

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

Good Luck

---

### Post by bscbrit on 2006-04-07
Found it - its in the plf repository:

The line to add to your /etc/apt/sources.list file would be:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

After you have done this, do
$sudo apt-get update

then 

$sudo apt-get install w32codecs

---

### Post by lesada411 on 2006-04-07
to get videos to play on the totem player? Do I have to download something so that i can play them? If so what is it and where can i find it. Thank-you

---

### Post by aysiu on 2006-04-07
Look at [the other thread you posted about this](http://www.ubuntuforums.org/showthread.php?t=156659).

---

### Post by bscbrit on 2006-04-07
Replying to your email....

Ok, click Applications -> Accessories -> Terminal

Once the terminal is open, type the following command:

sudo gedit /etc/apt/sources.list

It will ask you for a password - simply give it your usual password that you used when logging on.  'sudo' gives you God-like powers, which will enable you to edit the file - 'normal' users do not have permission to do this. (If you want to know more, type 'sudo' into the search box at the top of this page and press 'Go').

Add the line that I gave you in the previous post - copy and paste will save you typing it out and will help avoid mistakes.  Save the file, but leave the editor open until we know that you have done everything correctly.

Next, click on System -> Administration -> Synaptic Package Manager.  If it asks for a password, give it your normal password but it will probably have remembered it from the previous command. (If you take more than 5 minutes, it 'forgets' and will ask you again - this is entirely normal and is a good security feature)

Once Synaptic has loaded, press the 'Reload' icon near to the top left.  Let it do its stuff.  It is actually updating its list of available packages and making sure it knows what you already have.  Then press the Search icon and type in 'w32codecs'.  It should now find the correct package.  If you click on the package at the lefthand side it will select it.  Then press the 'Apply' icon.

Done!

Any problems - stop - think - and see if you can solve it. If not, come back here, I or someone else will be around to help.

---

### Post by ubuntu_demon on 2006-04-07
lesada411 please start 1 thread for each topic. I merged your threads.

welcome to our forums and good luck with your problems!

---

