---
title: "servername@server1:~$"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by 888mafia on 2008-03-06
Im in need of this type of set up.  Would anyone mind directing me to a tutorial on how to set up a radio server like this[[COLOR="Blue"]http://www.ubuntu.com/products/casestudies/KRUU[/COLOR]]("http://www.ubuntu.com/products/casestudies/KRUU")
I have just installed ubuntu 7.10 server correctly and am at the point where it says servername@server1:~$ and dont know what to do next

---

### Post by Nythain on 2008-03-06
hmmm... not quite sure, but i think its gonna take more than a simple online tutorial to take you from linux newb to running an FM Radio station...

ubuntu server doesnt install a GUI (otherwise referred to as Desktop Environment), they are a waste of resources that could be better spent "serving" things.

if you are completely unfamiliar with ubuntu and linux in general, you should start by typing from that command prompt
```

sudo apt-get install ubuntu-desktop

```
wich is a meta package that will basically install gnome and the entire "desktop" release of ubuntu... its really tough for a beginner to just "dive" right into command line management of a linux system... and at least with a gui you can utilize firefox to look up answers/solutions to problems, and you still have gnome-terminal to use to get used to all the different bash commands

and as for a tutorial on how to set up an FM Radio station, i really dotn know of any...

---

### Post by Origin415 on 2008-03-06
If you are looking to stream audio over the internet, you can try looking at software like peercast: [http://www.peercast.org/](http://www.peercast.org/)

For audio editing, audacity: [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

I'm not exactly sure what you are looking for, but it probably isnt in Ubuntu's server edition. That does not come with a graphical environment installed. You can get one without doing a full reinstall using the command:
```
sudo aptitude install ubuntu-desktop
```

Hope that helps.

---

### Post by 888mafia on 2008-03-06
The reason i tried ubunto is i was under thre understanding that is what i need for a dedicated server
i know how to run all the radio software which will be done on another computer  all i need is the stream
i think im explaining this right

---

### Post by steveneddy on 2008-03-06
I think you want icecast.

[Link here.]("http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html")
[B][COLOR="Blue"]
FYI - Icecast2 server is in the repos.[/COLOR][/B]

After you install the GUI ( Ubuntu-desktop )

Open synaptic

[B]System --> Administration --> Synaptic Package Manager
[/B]
click the upper right box and start typing "icecast"

You can get it there. Try it out and play around a little.

You are jumping to something that will not come easy. You are going to have to do a lot of work 
and you will have to learn a lot in a short amount of time to get this working properly.

But don't give up. You made it this far.

Edit:

I would run the "station" from the server.

Read the link above in this post.

---

### Post by 888mafia on 2008-03-06
> **steveneddy said:**
> I think you want icecast.

[Link here.]("http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html")

i have icecast i still need a server to connect to broadcast.   Icecast is installed on my pc it enables my software to communicate with the server so it is able to stream

---

### Post by steveneddy on 2008-03-06
> **888mafia said:**
> i have icecast i still need a server to connect to broadcast.   Icecast is installed on my pc it enables my software to communicate with the server so it is able to stream

Why don't you make the PC that icecast is installed on the server?

You are essentially streaming audio data from that PC anyway, just plug into the router and go man go!

This is what** I** would do.

You don't have to do what I would do, though.

The server you want will essentially do the same job as the router for broadcast.

You could use the server for serving and storing all of the music and associated files for you and just use the server as, well, a file server.

EDIT:

Try posting on the Multimedia or the Networking sections of this forum.

---

### Post by 888mafia on 2008-03-06
because the other computer is my lap top and it has all the broadcast software on it and all my apps 
i do more talk radio then music and it is from different  poker tournaments for example next  week ill broadcast from  Jacksonville 300 miles from home (server):) you see we right now i record the show through sound recorder and my buddy podcasts it through his server to my fforum

---

### Post by steveneddy on 2008-03-06
> **888mafia said:**
> because the other computer is my lap top and it has all the broadcast software on it and all my apps 
i do more talk radio then music and it is from different  poker tournaments for example next  week ill broadcast from  Jacksonville 300 miles from home (server):) you see we right now i record the show through sound recorder and my buddy podcasts it through his server to my fforum

cool

---

### Post by Nythain on 2008-03-07
ok, well you now have a "server"
The only thing that makes ubuntu server a "server" is it lacks a GUI (they are a waste on servers, unless its a "learning" server) and it configures Apache, MySQL, php during install.

from there, i mean, whatever server or daemon you are needing to stream to your laptop for broadcast (im assuming thats how you are doing it, im still a bit confused as to what you are ultimately looking for) can be installed from what you have going on now, or possibly requires a Desktop Environment to run

people have suggested icecast to run on the "server" to stream whatever it is you need off of the server to where ever it is you need it to go, that sounds like a good idea... you say you have icecast on your laptop already, as part of your broadcasting utilities, so now im not sure what exactly you need your "server" to do...

do you just need it to store files??? do you need it to host a website??? do you need it to stream audio/video??? do you need it to track torrents??? where you wanting to podcast from your server to your forums instead of going through your buddy???

So far i have gathered that you
1. go to location (usually poker tournaments, maybe sometimes home, etc) and do your recording on your Laptop
2. send recording to your friends server where he
3. podcasts it to
4. your forums for the rest of the internet to listen to

that sounds pretty hip, but it also sounds like you have everything you need, so thats where im getting confused as to what you want the "server" of yours to do exactly

once i/we know exactly what it is you are trying to get this machine to accomplish, i/we can probably point you in the right direction

---

