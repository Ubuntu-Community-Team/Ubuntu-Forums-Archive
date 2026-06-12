---
title: "error when installing package"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-04-30
i'm trying to install gdisklets but when i open the package i have downloaded from the internet and open it with g dpi it comes up with an error - dependency is not satisfiable.
How can i fix this?

---

### Post by Nythain on 2007-04-30
install whatever dependency is it saying is unsatisfiable???

---

### Post by Dark-Angel on 2007-04-30
> **Nythain said:**
> install whatever dependency is it saying is unsatisfiable???
I'm not really sure ho to do that.

---

### Post by Nythain on 2007-04-30
what dependency did it list as unsatisfiable, to be more precise... could you paste the exact output... so we can see if you just done have the dep. or if its either to high or to low of a version???

---

### Post by Najand on 2007-04-30
Try this command and see if it is part of the repositories or not:
```

$ aptitude search FOO

```
Change FOO with your package name. If it is available there, you can download it easily without any problem using:
```

$ sudo apt-get install FOO

```

---

### Post by Nythain on 2007-04-30
heh... here i get so carried away trying to answer the question that i completely dont even think about recomending sudo apt-get install gdesklets to install it and its dependencies automatically :)

---

### Post by Dark-Angel on 2007-04-30
[IMG]http://i16.photobucket.com/albums/b21/cam_m/Screenshot.png[/IMG]
Thats the error i'm getting
It is hard not haivng the internet on my ubuntu machine as i need to find the files i want and trasnfer over.

---

### Post by Najand on 2007-04-30
well there are alot of dependencies. I recommend you to enable UNIVERSE/MULTIVERSE repositories and download it using them. It is easy and just takes a few minutes.
> Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.12.2), libbonobo2-0 (>=
         2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2
         (>= 1.2.4), libfontconfig1 (>= 2.4.0), libgconf2-4 (>= 2.13.5),
         libglib2.0-0 (>= 2.12.0), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>=
         2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.16.0),
         libgnomevfs2-0 (>= 2.16.0-1), libgtk2.0-0 (>= 2.10.3), libgtop2-7 (>=
         2.14.2), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.1), libpango1.0-0
         (>= 1.15.2), libpopt0 (>= 1.10), librsvg2-2 (>= 2.14.4), libsm6,
         libx11-6, libxcursor1 (> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1),
         libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxrender1,
         python-gnome2 (>= 2.0), python-gtk2 (>= 2.0), python-numeric (>=
         23.0-7), python, python-xml, python-pyorbit, gdesklets-data

---

### Post by Nythain on 2007-04-30
> **Dark-Angel said:**
> 
It is hard not haivng the internet on my ubuntu machine as i need to find the files i want and trasnfer over.
so that answers why they dont just enable the repos and apt-get it...

---

### Post by Najand on 2007-04-30
I see... then you should download all those packages and try ```

sudo dpkg -i FOO1 FOO2 FOO3 ....

```

---

### Post by Nythain on 2007-04-30
thanks for the dpkg command... i was gonna recomend that solution to get a list of unmet dependencies, but since i have the internet, and apt-get everything im not to familiar with the syntax for installing deb using dpkg

---

