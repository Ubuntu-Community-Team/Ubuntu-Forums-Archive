---
title: "Wireless mighty mouse lost scroll"
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by rifak on 2008-07-01
Hey everyone,

I have had my wireless mighty mouse up and working fine for a few days now. But, I logged in today and the scroll doesn't work, and my bluetooth icon is no longer in my tray. If i can get some help, that would be great. thanks!!

---

### Post by rifak on 2008-07-01
this has been solved. i restarted my computer and everything was working again.

---

### Post by RRR-007 on 2008-07-03
Hey

  How did you set up your wireless mighty mouse scroll to work with ubuntu initially. I have the same kind of mouse but only the left  & right click functioning but not the scroll option with ubuntu. if you wud have done any extra steps to enable scroll in ubuntu, it wud be of great help.....

---

### Post by rifak on 2008-07-03
everything in parenthesis are just explaining what each thing does. open up terminal and do the following:

(scans for device, outputs a number)
             hcitool scan

(add device to hcid.conf)
             sudo gedit /etc/bluetooth/hcid.conf

(when file opens, add the number you get with the hcitool scan command)
(add it like this to the hcid.conf file, replacing NUMBER with the number you get:

             device NUMBER {
             name "Mouse" :
             }

(save, and close file)

(then back to terminal: )

(to restart bluetooth)
             sudo /etc/init.d/bluetooth restart

(search for your mouse)
             sudo hidd --search


hope this helps..and not too confusing.

---

### Post by RRR-007 on 2008-07-03
hey thanks for throwing up the soln... unfortunately i spent all of my time today playing around kiba dock on my machine but of no luck... i'll try your suggestions and keep you posted the results..

---

