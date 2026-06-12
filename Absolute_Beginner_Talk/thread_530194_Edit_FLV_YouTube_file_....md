---
title: "Edit FLV YouTube file ..."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-08-20
I need to edit an *.flv file that I got off of YouTube.  
Would someone recommend an application that can do this?

Thanks

Carl

---

### Post by Jamie Jackson on 2007-08-20
There's probably a better way, and I'm looking for a Linux FLV convertor myself, but there are [site]("http://media-convert.com/")s that convert to the format of your choice for free.

I've used avidemux for pulling out segments of video (never did any real "editing"), but it worked great for my purposes.

---

### Post by sentientmachine on 2008-03-03
I was able to edit a .flv video to cut out the first few seconds with the program avidemux

Here is how I did it:

Install avidemux:
as root:  yum install avidemux
or
sudo apt-get install avidemux

Run the program, it showed up for me in the start menu under multimedia -> "avidemux video editor (QT)"

Choose open, open the .flv file you want to edit, parse or convert.

Press play, and the video should play, get the frame number where you want to begin copying.  Get the frame # of where to start.

Choose edit-> set marker A

Move the slider to the spot where you want the parsing to end.

Choose edit-> set marker B

To save your clipped .FLV file, choose File->save->save video.

Save your file as something.flv

Play the something.flv file with vlc and your parsed video plays.

---

### Post by vegardjo on 2008-04-10
after using a day on this I'm just posting my results here for reference:

I'm both a novice Linux user and video editer, so I still like my GUIs, and don't know much about codexes. 

my goal here was to edit a wmv source file and then get it to flv format so I could use it online. I had the file as flv aswell, but unedited. 

I did not manage to open the flv directly in Avidemux, so I had to open the wmv instead. after editing this was saved as avi. 

then I tried to convert the avi to flash with ffwin ([www.ffwin.org](www.ffwin.org)), which gave me poor results. so, after a few hours of trying everything I decided to take the avi, convert it back to wmv in ffwin, and then convert the wmv back to flv again. 

...and that worked quite nice, hope that can be of help to someone :)

---

