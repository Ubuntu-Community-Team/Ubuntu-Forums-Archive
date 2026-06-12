---
title: "Can i make a server for on demand videos on my local network"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-29
Hello 
with vlc can i make a server that will just sit there until i request a video to be played from it, the reqest would be made from a remote computer on my local network.
then the server would start to stream it on that network to the computer.

i all ready know how to set up a stream with vlc if i am on the server and how to open it on the client with vlc.
:) 
mythbuntu?

---

### Post by MrFSL on 2007-10-29
Sure. Through some clever cgi scripting you can manipulate applications on your server using a web interface. 

The issues become ones of security.

You would have to be mindful of the number of times or instances of the vlc application on the server. You would also have to have some sort of smart application termination on the server.

An advantages of a web based server interface in that you could use the built in variales to direct traffic to the connecting client IP etc.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-30
Thank you for the advice .... but i read it and i think i under stood most of it, however how ever i don't have anuf skill to implement it.
lol i will give it a shot but i was hopping for more of a install this ... tada :)

But thanks agin

so whats cgi i am going to google right now but ....
edit : Common Gateway Interface

---

### Post by MrFSL on 2007-10-30
Sorry.

Perhaps if you let us know how you plan to use this server. 

If you are just interested in streaming audio or video in your local network there are a few ways to accomplish this. If you are interested in streaming video across the great world wide web - well that's another story.

My original answer could be explained like this:
Install apache2 web server. Configure up a web server. Then build a special web page using a scripting language like perl to interact with the person accessing the web page.

It might be overkill if you are just looking to play video across you local network. You could just setup a local file share and double-click the file you want when you want it. Or you could terminal into a local network machine and run a little script that would start vlc.... the options are endless but tailoring it to your specific needs would require a better knowledge of what you want to accomplish.

P.S.
And I am sorry for the geek-speak.

---

### Post by hyper_ch on 2007-10-30
How about just mounting that remote directory in your local file system?

Also have a look here:   [http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-04
just home network uses
 if i just mount the share then it seems to glich more then if I tell vlc to stream and the open the stream on another computer.

what i would like to do
On any computer(windows or linux) in my home assess any the movies on my "movie server" with out having to start the stream when i am at the "movie server" 
i would also like it to be fool prof so my family can use the movie server

---

### Post by MrFSL on 2007-11-04
This can be done using ssh.

The first thing I would do is write a script on the server that starts the stream from the command line.

Then I would write a script on the client that opens an ssh session, and runs the script on the sever.

It shouldn't be too hard to bash it out.

I'm not too familiar with vlc or I might be able to supply you with some sample scripts.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-05
> **MrFSL said:**
> This can be done using ssh.

The first thing I would do is write a script on the server that starts the stream from the command line.

Then I would write a script on the client that opens an ssh session, and runs the script on the sever.

It shouldn't be too hard to bash it out.

I'm not too familiar with vlc or I might be able to supply you with some sample scripts.

sounds like a reasonable way to do what i would like
I am trying to figure out vlc's command line options right now
very confused i cant under stand the sintax
This  is the site i am looking at
[http://www.videolan.org/doc/streaming-howto/en/ch03.html](http://www.videolan.org/doc/streaming-howto/en/ch03.html)
i would like to know how to stream using http and the thing to keep the connection open wile switching between files on the play list   something about --keep-sout

if someone could show me a few examples of working commands i am shure i could get it

---

