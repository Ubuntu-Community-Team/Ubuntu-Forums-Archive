---
title: "How do I access other servers where I have accounts?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by sailorstud on 2007-05-25
Just installed latest UBUNTU.. was pleased with the process.
I am taking Comp Science courses at FSU, and prior to installing UBUNTU, I would access the servers using a SSH client running under XP. The server address is program.cs.fsu.edu.    

How do I access this server now, under Ubuntu?  I see a ssh command.. but am not having any luck with using it.

Any help will be appreciated.  Paul

---

### Post by Ek0nomik on 2007-05-25
```
ssh username@program.cs.fsu.edu
```

or

```
ssh -X username@program.cs.fsu.edu. 
```

this will load the X window environment so you can run programs that aren't installed locally on your local computer.  it's pretty cool.  ;)

---

### Post by sailorstud on 2007-05-25
Thanks for your quick response.  I did try both of your suggestions, to no avail.  It does not seem to find the server.  (I know the server address is valid.. as I can access it from my xp machine using SSH for windows.)

Could it be that I have to do some prep work first, like generating a hash key?  or some configuration work?   There are a lot of options.  

I am having fun exploring this new territory, and look forward to getting a development environment (maybe eclipse) up and running under ubuntu.  

Again, Thanks.. Paul

---

### Post by vanadium on 2007-05-25
There should not be any other requirement than a working internet connection for connecting using ssh. Is your internet connection working correctly for other applications?

---

