---
title: "Celestia: Root permission"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by atenlaugh on 2006-07-13
So, I'm trying to get Celestia set-up, but am constantly confronted with having to work around file permissions. I'm not afraid of the command-line, but for something like this, the GUI is honestly faster (all of Celestia's add-ons are drag-and-drop, or very simple modifications). I know about sudo and gksudo nautilus, but then I would have to go into every file of Celestia's, and change ownership to each of them, and that seems to work in a quirky manner anyhow. 

Isn't there a way I can tell it to be able to use the "Celestia" directory AND all sub-directories as readable and writable, even the new stuff I put in?

---

### Post by aysiu on 2006-07-13
I don't even know what Celestia is, but you can change ownership of the directory and sub-directories.

For example, if it's on your desktop: ```
sudo chown -R atenlaugh:atenlaugh ~/Desktop/celestia
```

---

### Post by mcduck on 2006-07-13
You don't need to change any permisssions if you use 'gksudo nautilus' to open file manager with admin privileges and copy your addons to celestia folders that way.

That's how I did it, and I sure didn't change any permissions at any point. (anyway, changing permissions for anything outside your home directory is usually a very bad idea)

---

### Post by aysiu on 2006-07-13
Oh, is Celestia outside the home directory? I don't even know what Celestia is...

---

### Post by atenlaugh on 2006-07-13
Mcduck, I was just wondering if there was a way to go about it without doing that, but I guess the security issue you brings up makes sense! Learning more and more. :D 

Aysiu, I read the "chown" man, and I think that would do what I was originally considering, but as was brought up, I think I'd like to be as safe as possible, so...thank you!

Celestia is a space-simulation/astronomy program: [http://www.shatters.net/celestia/](http://www.shatters.net/celestia/)

Anyway, it's very, very cool.

---

### Post by mcduck on 2006-07-13
> **aysiu said:**
> Oh, is Celestia outside the home directory? I don't even know what Celestia is...
Then you should try it, it's amazing!

> 
Unlike most planetarium software, Celestia doesn't confine you to the surface of the Earth. You can travel throughout the solar system, to any of over 100,000 stars, or even beyond the galaxy. 

All movement in Celestia is seamless; the exponential zoom feature lets you explore space across a huge range of scales, from galaxy clusters down to spacecraft only a few meters across. A 'point-and-goto' interface makes it simple to navigate through the universe to the object you want to visit. 

Celestia is expandable. Celestia comes with a large catalog of stars, galaxies, planets, moons, asteroids, comets, and spacecraft. If that's not enough, you can download dozens of easy to install add-ons with more objects. 

link: [http://www.shatters.net/celestia/]("http://www.shatters.net/celestia/")

---

### Post by atenlaugh on 2006-07-13
"You can travel throughout the solar system, to any of over 100,000 stars..."

Currently expandable up to 2 million. Awesome. 

(not to turn this into a gush-about-celestia thread or anything...)

---

### Post by aysiu on 2006-07-13
I'll check it out.

---

