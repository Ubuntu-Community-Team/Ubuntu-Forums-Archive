---
title: "Trying to run Planeshift...."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by blueshark.oo7 on 2007-06-30
well I got past installing it, so I tried to open it, by using this command:

sudo /opt/PlaneShift/psclient

and this is what I get:

/opt/PlaneShift/psclient: line 6: /opt/PlaneShift/psc: cannot execute binary file
/opt/PlaneShift/psclient: line 6: /opt/PlaneShift/psc: Success

and then nothing happend

Anyone help me out here?

---

### Post by isaacj87 on 2007-06-30
Look for the PlaneShift folder in your Home folder...there should be an executable in there.

---

### Post by farueulogy on 2007-06-30
> **blueshark.oo7 said:**
> well I got past installing it, so I tried to open it, by using this command:

sudo /opt/PlaneShift/psclient

and this is what I get:

/opt/PlaneShift/psclient: line 6: /opt/PlaneShift/psc: cannot execute binary file
/opt/PlaneShift/psclient: line 6: /opt/PlaneShift/psc: Success

and then nothing happend

Anyone help me out here?

Pretty awesome coincidence - I set this game up today.

My command is this cause I installed everything to my home folder:

> 
sudo /home/james/.planeshift/./psclient

**I *assume* your code would be:**

> 
sudo /opt/PlaneShift/./psclient

I assume you need that extra ./ in there

---

### Post by Forumdude on 2007-07-05
I had the same problem.

> elampe@elampe-desktop:~/.PlaneShift$ sudo ./psclient
./psclient: line 6: /home/elampe/.PlaneShift/psc: cannot execute binary file
./psclient: line 6: /home/elampe/.PlaneShift/psc: Success

I got  to the folder and tried to execute the file, but It just didn't work.
](*,)

---

### Post by le garcon solitair on 2007-07-15
i've tried what you guys have tried and i just get

> 
tyler@tyler-desktop:~/PlaneShift$ sudo ./psclient
./psc: error while loading shared libraries: libcal3d.so.12: cannot open shared object file: No such file or directory


---

