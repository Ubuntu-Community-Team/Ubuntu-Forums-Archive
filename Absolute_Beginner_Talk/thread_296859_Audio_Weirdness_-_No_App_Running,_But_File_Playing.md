---
title: "Audio Weirdness - No App Running, But File Playing!"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by elcasey on 2006-11-10
I decided to finally delete the .ogg of Ep.75 of TWiT since it wasn't really my style (I don't need it without Dvorak ;)). So I highlighted it, and pressed "Del".

Now I'm hearing TWiT 75 over top of the internet radio I was listening to via XMMS. But it's not in the XMMS playlist, and there's no other audio apps running. I even closed XMMS, started Beep and Rhythmbox...nothing in either.

So what the hell is going on? I even emptied the Trash and it's still playing!

---

### Post by elcasey on 2006-11-10
I know most of you probably thought I was an idiot and didn't check the other workspaces, but I swear I did.

I just logged out and back in, but it was really weird. What (and where?) is the Linux equivalent to the Windoze Task Manager? At this point, it's just curiosity.

---

### Post by angryfirelord on 2006-11-10
System-->Administration-->System Monitor

What happened was your player was in the background and file was in the cache or in a tmp (temporary files) folder. Logging out would have shut down the player.

---

### Post by elcasey on 2006-11-11
Come to think of it, I don't remember if I checked the system tray or not. But I don't think BMP was running. Anyway, thanks, Firelord! :)

---

