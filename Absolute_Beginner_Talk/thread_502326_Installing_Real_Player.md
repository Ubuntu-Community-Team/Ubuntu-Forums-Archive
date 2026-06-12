---
title: "Installing Real Player"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-07-16
Hello

I have installed RealPlayer and can use it to view streams from the BBC News site. However I can only do this in stand alone mode. I initially get an error that tells me that "...hxplay or realplay cannot be found in the system path..."

1 What is the system path?
2 How can I find hxplay or realplay?
3 How can I move hxplay or realplay into the system path?

Thanks,
Bob

---

### Post by Famicommie on 2007-07-16
The system path is a list of directories where executables can be found. For instance, if I install a program to the directory /opt/directory cannot execute that program simply by typing programname. If I want to run that program as it stands in /opt/directory/ I would have to type out the absolute path: /opt/directory/programname

Linux only knows to look for executables in certain places.
/bin contains programs necessary for running linux (e.g. ls and mkdir)
/sbin contains programs specific to system administration
/usr/bin contains the executables to "extra" programs (e.g. firefox and evolution).

If you click on "Places", select "Find Files", and specify "Look in folder: Filesystem" you can do a search for realplay or hxplay. Make a note of the location and open a terminal up. Then simply make a symbolic link in /usr/bin to the real location of the binary file. Suppose that realplay is installed in your home directory in a directory called realplay. Then the command would look as such:```
ln -s /home/user/realplay/realplay /usr/bin/realplay
```

---

### Post by bwallum on 2007-07-18
Thanks Famicommie, at last I get succinct and precise advise, thank you very much indeed.

I am now beginning to understand the file structure and how to find files and folders. That has been a great move forward for me. I don't yet have realplayer running properly, but one step at a time.

My goal is to get the BBC News streams found on [http://news.bbc.co.uk/](http://news.bbc.co.uk/) (where it has "watch" buttons). I currently have the Linux RealPlayer10GOLD.bin file on my desktop. I would like to get it installed in to /usr/bin I guess. I presume the video player (Mplayer) then needs to know the path to it. I'm using Firefox as the browser.

So, if you would bear with me, could you please help me with:-

How do I install from the .bin file on my desktop to the /usr/bin directory?
How do I tell the Player where the realplay and hxplay files are?
Do I need anything else like a browser plug in to make it all work?

Thanks again for your very professional help, it is a breath of fresh air.

Kind Regards
Bob

---

### Post by Qui on 2007-07-19
hi, 

to install real player  log in as root or a super user, go into the directory where the real player binary (.bin) file is locates via a terminal and type the command 

# chmod +r *real*.bin
to make the binary file executable and

# ./*real*.bin   
to run the executable file.

you will be prompted for a destination path during the installation as in where would you like to put real player. you may enter (/usr/sbin/)

in case you you did not provide this path but instead chose to put the files on your desktop during the installation of real player then you would have to create a symbolic link to real player by typing 

# ln -s <path to real player> /usr/sbin/realplayer

good luck,
qui

---

### Post by RomeReactor on 2007-07-19
Hi. you can also install RealPlayer as root, so you don't have to make the symbolic link:
```
sudo ./RealPlayer10GOLD.bin
```

---

### Post by bwallum on 2007-07-19
Hi all

Well I have been around the houses with this one but now understand a lot more about Linux and the way it handles files.

I have given up on RealPlayer, I could only ever get it to run in stand alone.

However I have installed Mplayer and by some co-incidence it worked. I now get a very good embedded video with Mplayer when watching BBC News. 

Thank you all for your assistance. Linux is very complex and it seems you have to have a deep knowledge of how it works in order to get things to work for you. Or you just get lucky fiddling. My experience here seems to fall in the latter category.

Many thanks again
Bob

---

