---
title: "Help useing vlc's command line to stream video on local lan"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-05
Ya soooo 
if anyone is really good with vlc's command line i need your help :)
say i have a movie @ /home/joe/movies/mymovie.avi
and i would like to stream it over my local lan to a nother computer useing vlc's http thingy through the command line how could i do this

---

### Post by P4man on 2007-11-08
[http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html](http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
yes thats the gide i have been looking at it's just it dosent seem to work when i try thoughs commands 
so i figured that i must be messing it up lol
i really would apresate an example thats not just 
# vlc --blaaaa [<"your stuff here">] 
becuses i dont know if i need the[]<>"" and the other stuff they have in there i under stand that you have to change the your stuff here part but should i get rid of the "" thingys 
this is why an examples would be perfict 
thanks :)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
heres the command the help file says i should use
vlc -vvv input_stream --sout '#standard{access=http,mux=ogg,dst=server.example.org:8080}'

so if i have this
file path /home/joe/Funnystuff.avi
my ip 192.168.2.5
port 1234

then i should use this ?

vlc -vvv /home/joe/Funnystuff.avi --sout '#standard{access=http,mux=ogg,dst=192.168.2.5:1234}'

i dont know if i need the ' and the  # and the last '
also the mux=ogg  do i need this if i dont care what kind of package it puts it in, i mean its in an avi why not keep it that way
agin thanks for the help

oh and then the client side i can just use the gui to open the stream

---

### Post by Bigbird999 on 2007-11-11
joe
I use VLC to play media from a remote computer all the time.  That is I "pull" the video from a remote computer.  Why do you need to "push" video to the remote computer??  

I installed VLC on my laptop, I mount a window share directory where my videos are stored and open the file I want to watch with VLC.

Is this what you want to do??



BB

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
yepp thats exactly what i would like to do but when i just pull it from another computer it just cindof gliches 
like it drops 3 second of video loss of sound then comes back
so if i push it it has no problems 
i know how to use the gui but i cant get the command line 
i would like the command line cuse then i can ssh into the remote computer and tell it to play stuff

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
ok so back to banging my head on a wall

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-23
bum

---

### Post by ninocass on 2007-11-28
Hey joe been working on this myself

so far i have this working

```

 vlc -vvv -I http <path to video> --sout '#standard{access=http,mux=ts,dst=<server addresS>:<server port>}'

```

should do a job, ill write a nice script that you only need to pass a file name too later ;)

---

### Post by ninocass on 2007-11-28
okay heres a script for streaming the video:

create the script file:
```

touch stream_video

```

edit the file using your editor of choice
```

gedit stream_video

```

paste in the following
```

#! /bin/bash

vlc -vvv -I http $1 --sout \#standard\{access\=http\,mux\=ps\,dst\=<server address>:<port>}

```
You need to replace the server address with your local ip and pick a port (i use 1234, easy to remember)

close gedit and run

```

sudo chmod 777 stream_video

```

and finally stick the file in your bin

```

mv stream_video /usr/bin

```

all you do i call the script and pass a path to a video ie

```

stream_video /media/storage/sample.avi

```

sorted!

---

