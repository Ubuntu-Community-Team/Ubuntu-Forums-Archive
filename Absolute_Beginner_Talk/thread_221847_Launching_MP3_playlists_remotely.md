---
title: "Launching MP3 playlists remotely"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by calagan on 2006-07-24
I have a Ubuntu Dapper server in my living room with no keyboard or monitor, that I mainly use as a file and Web Server (Apache/PHP/MySQL/Python are installed) and I wonder if it would be possible to launch MP3 files or playlists remotely, through terminal or a Web page and that the sound would come out of the speakers locally on the Ubuntu server.

Thanks in advance for your help,

Cal

---

### Post by risbac on 2006-07-24
Mmmm ssh to the server, then vlc /path/filename?

It's working for a .mp3 and seems to be OK also for playlists.
Should work also for other player if you don't like vlc.

---

### Post by mcduck on 2006-07-24
What you ned to do is install MPD (music player daemon). It's great music player that can be controlled with various clients through networks or anything..

Take a look here: [http://www.musicpd.org/]("http://www.musicpd.org/")

There are also lots of information about MPD in these forums, you could try search for some nice HowTo's and more :)

---

### Post by risbac on 2006-07-24
But he doesn't want to play music on clients, am I wrong? 
He wants to play them on the server directly, so no need for a service or anything related to clients. Tell me if I'm wrong Calagan?

---

### Post by calagan on 2006-07-24
Thanks for your concern risbac, you're right about what I'm looking for (playing music on the server and not on the client), but from what I read on [http://www.musicpd.org](http://www.musicpd.org), I believe that MPD does fit the bill . The client's purpose is just to pilot MPD while providing a fancier interface than terminal, but not to play the music.

Update: I've tested MPD and it works like a charm, thank you guys.

---

