---
title: "cURL and tty"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by dilbert92 on 2007-11-14
Hey all!

I just got an Arduino last weekend. I love it, it's awesome! I'm trying to make a web hit counter with it.

To do this I've, made a PHP counter on my site that saves the number of hits to a file called count.txt. 
Then I use cURL to grab the data and save it locally. 
Then I use a serial terminal to post the data to the Arduino.
Perfect! But I have to do the cURL and serial terminal manually.

So how do I make cURL automatically update every second or so? My command looks like this:

curl [http://www.mysite.com/count.txt](http://www.mysite.com/count.txt) -o home/USERNAME/Desktop/count.txt -y 1

Also, is there a serial terminal for Linux that can send a file repeatedly? The only one that I've come across is MTTTY for Windows.

Thanks!

-Zakk

---

