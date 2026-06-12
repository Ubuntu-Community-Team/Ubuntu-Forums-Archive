---
title: "ogg to mp3?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-28
is there one that has a GUI?

i have lots of songs in this format and its gonna be hard doing this in the terminal....

---

### Post by calvinthomas on 2006-08-28
I asked a similar question previously and the answer is yes! Its called gnormalize.

It normalises volume of tracks but also outputs in many formats, will do many tracks in one go also.

If you want to do more than just straight change the format, i.e. editing, I recommend Audacity, its very simple to use and very good!

Calv

---

### Post by L_o_N_e_R on 2006-08-28
w00t w00t thnx man :)

---

### Post by L_o_N_e_R on 2006-08-28
i cant find a Deb package -.-

---

### Post by Toxicity999 on 2006-08-28
sudo apt-get install soundconverter

It doesn't depend on what it needs for mp3 conversion... though when you use it from terminal by typing soundconverter it will give you an error of what package it needs to have mp3 functionality.'

Once you have that working open preferences set what you need for output options and tick mp3 for output.

Now what isn't so fun about soundconverter is it relies on gstreamer .8 us now using .10 so you need to install a whole mess of basic gstreamer packages that only the converter uses.. but this is a pretty good utility though for me it doesn't like overwriting files... like when I try to lower quality or something it deletes the fiel it needs to read from first haha.

---

### Post by calvinthomas on 2006-08-29
Have you added the universe repositories? its in my synaptic but I do have a huge sources list these days.

Its definately in these repos, go to a terminal and follow these commands:

sudo gedit /etc/apt/sources.list

Add this to your sources list:

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

Save the changes and enter this command :

sudo apt-get update

Now you'll be able to install it with synaptic, to see what else is available in this repo see: 

[http://asher256-repository.tuxfamily.org/index.php?page=packages&lang=en](http://asher256-repository.tuxfamily.org/index.php?page=packages&lang=en)


A Second method:

Go here: [http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

Download the .rpm (at the bottom) to your desktop

Go to a terminal

Type sudo alien and then drag and drop the downloaded file in to the terminal (this will put the name of the package next to sudo alien i.e. something like: sudo alien cd /home/<name of user>/Desktop/<Name of file>

Press enter and enter your password

This will create a deb on your desktop, then double click it and press install.

NOTE: If you can't use alien download it from synaptic (type alien into synaptic)

NOTE 2: The first method is slightly preferred as the second may require you to install a list of dependencies which you may need to download aswell

NOTE 3: The alien command is really useful to learn!

Calv

P.S Sound Konverter is a good option also, I had a couple of problems with it but I was converting some (not too good) wav files to mp3 and others seem to have had absolutely no problem with it.

---

### Post by Toxicity999 on 2006-08-29
Other than the issue about overwriting files yea the one I got from the repos named soundconverter works pretty well. The per file completion bar even updates in pace.

---

### Post by JayTee on 2006-10-18
I've used Audacity and it has many capabilities for editing as well as conversion but for easy, simple conversion I prefer Soundconverter. If you install it from the repositories you'll also need to get gstreamer-lame plugin to enable conversion to mp3. I'm pretty sure you need to enable the universe multiverse repositories for that but I'd already done that for other software and left them enabled. I had to go into the Advanced option of Add/Remove and search for LAME. If it doesn't find one named gsteamer0.8-lame then you don't have the right repositories enabled. Once I applied this library I could convert to mp3 and it works like a charm.

---

### Post by easy_target on 2006-10-18
I believe soundconverter in edgy doesn't depend on gstreamer 0.8 anymore.
Give it a try and see if it fits your needs.

---

