---
title: "Rhythmbox music player has just freaked me out"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-05-12
Rhythmbox music player has just freaked me out. On the source column, at the very bottom is what appears to be another users mp3 collection (and someone local as its in my language (Finnish)) and I can access their music.
WTF?
Is this normal? 
Do they have access to my stuff?

---

### Post by starcraft.man on 2007-05-12
> **r3bol said:**
> Rhythmbox music player has just freaked me out. On the source column, at the very bottom is what appears to be another users mp3 collection (and someone local as its in my language (Finnish)) and I can access their music.
WTF?
Is this normal? 
Do they have access to my stuff?

Ummmmmmmmmmmmmmmmm.... Now thats one I've never seen before. Far as I know, rhythmbox only adds music from the folder you point it to...

Can you readd your music to another player like amarok or banshee does it happen there? Are you connected to any other computers in your vicinity via samba? If you are, can you dissable all samba shares and see if the files are still there? If so, they are local and got on your comp somehow... Files don't just appear out of thin air last I checked >.>. Nor do I think a hacker would give you music files...

---

### Post by weresheep on 2007-05-12
Hello,

Rhythmbox has the ability to allow people on the same network to share their music with each other, similar to iTunes. Other people's music files aren't actually copied to your computer, but are streamed (like an online radio station) to your computer when you play them.

If you look in the Rhythmbox preferences (Edit / Preferences) and look in the Share tab there is an option for allowing other people to view your music. If this is turned off then no one should be able to see or play your music. As you can see someone else's music it seems someone else on the same network as you is using Rhythmbox with that option enabled.

I don't have an option in my old Rhythmbox (version 0.9.3.1) to turn off looking for other peoples music, but perhaps you do?

-weresheep

---

### Post by r3bol on 2007-05-12
I'm still fairly new to Linux and I've just installed 7.04 on this computer. I connect through what is called a residential gateway (I think). That is an ethernet cable into the wall, which goes to someplace in the apartment block. Everyone is connected to this place. I haven't actually set up any other players yet so I can't test that just yet. As for the Samba thing, I know its a server, but I haven't touched it. I don't even know if I have it or where it is located.

If I click file>properties>details>location = daap://85.194.214.96:5214/databases/1/items if that helps any.

If its a share thing, then is ok i guess. As long as this person doesn't have access to my whole machine! What is interesting is an option to delete the tracks, although I haven't tried it.

---

### Post by r3bol on 2007-05-12
There is also no option for sharing music in my prefs. I am using version 0.10.0

---

### Post by starcraft.man on 2007-05-12
> **r3bol said:**
> I'm still fairly new to Linux and I've just installed 7.04 on this computer. I connect through what is called a residential gateway (I think). That is an ethernet cable into the wall, which goes to someplace in the apartment block. Everyone is connected to this place. I haven't actually set up any other players yet so I can't test that just yet. As for the Samba thing, I know its a server, but I haven't touched it. I don't even know if I have it or where it is located.

If I click file>properties>details>location = daap://85.194.214.96:5214/databases/1/items if that helps any.

If its a share thing, then is ok i guess. As long as this person doesn't have access to my whole machine! What is interesting is an option to delete the tracks, although I haven't tried it.

Ah, I see what it is. Your whole apartment is wired on one network, and you are not switched so your each segmented. I guess the place wanted to be cheap and put everyone on the same network. That is bad, well for others, I doubt someone else could reach into your machine, I assume the files you get are from an open Windows box thats plugged right into the internet and doesn't have a firewall... thats very bad, that user must have viruses...

I doubt its anything to worry about for you, your neighboor though with open sharing should be concerned... VERY!

---

### Post by aeiah on 2007-05-12
someone else on your residential gateway will have file sharing enabled. i think itunes likes to do it

---

### Post by r3bol on 2007-05-12
I checked my 'Shared Folders' via system>admin and it says that I dont have the services installed yet. Can I see if I can access any other places on their machine? If they are open to every one here, I think I should warn them about it. 

Just to check, if I don't have the sharing services installed yet, then my stuff is private - right?

---

### Post by tageiru on 2007-05-12
> **r3bol said:**
> I checked my 'Shared Folders' via system>admin and it says that I dont have the services installed yet. Can I see if I can access any other places on their machine? If they are open to every one here, I think I should warn them about it. 

Just to check, if I don't have the sharing services installed yet, then my stuff is private - right?

[http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol](http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol)

It has nothing to do with system->admin->shared folders. It is managed from within rhythmbox. If you haven't activated daap sharing in the plugin section you should be fine.

---

### Post by r3bol on 2007-05-12
Ahaa, so its in the plugins and yes it was enabled. Can't remember if it was by default, I did run through the settings once. 

Well I can sleep easy tonight,
Cheers.

---

