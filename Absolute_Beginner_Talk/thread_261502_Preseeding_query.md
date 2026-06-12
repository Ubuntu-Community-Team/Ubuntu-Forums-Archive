---
title: "Preseeding query"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-09-20
Hi

I am looking to automate the install of Ubuntu onto my laptop. I have read the offical howto on the ubuntu help site but have run into a bit of a quandry. I need to create a preseed file and I am a little unsure what to do. The howto says to use the examnple at this link: [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs01.html](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs01.html)

What I am not sure about is do I need to have the whole lot in the file or only include the d-i lines that I want to specify? Will the rest of it then follow the normal defaults? I have done the ubuntu install a number of times now so I know that there is only really 4-5 questions you need to answer to complete it so does that mean I only need to have 4-5 lines int he preseed file? Is there a list anywhere of all the questions that can be answered a bit like the windows deploy tool?

cheers
niteblind

---

### Post by bazzer on 2006-09-20
I'm right on a similar track at the moment!

Maybe I'm stating the obvious here, but every line that begins with a hash '#' is a comment. So if you wanted to remove the lines that are 'commented out' it will still work. Most people leave them in though. Myself, if I want to include a line, I'll add it specifically in the location below the commented out example.

HTH

---

### Post by niteblind on 2006-09-21
anyone know how i can use this command?
debconf-get-selections --installer > file

when i try to run from a basic terminal bash cannot find the above. The guide says that you can run this after install but if it is a separate program when should i do this?

niteblind

---

### Post by bazzer on 2006-10-27
I think you can do this as soon as you can login. If it doesn't work, try apt-getting 'debconf-utils' (I think - not near a working linux box atm) then trying again?

---

