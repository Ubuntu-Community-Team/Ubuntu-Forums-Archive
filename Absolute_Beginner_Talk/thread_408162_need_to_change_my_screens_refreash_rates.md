---
title: "need to change my screens refreash rates"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jrcullen007 on 2007-04-13
need to change my refreash rate from 85 hrtz to 75. don't really know how to do this and make it stay. i can change it under my prefs but that doesn't take when i load up the comp. just goes back to 85 any help would be nice

---

### Post by dunedust on 2007-04-13
you will have to edit your xorg.conf file

*sudo gedit /etc/X11/xorg.conf*

under the  monitor section you can  edit the refresh rates

---

### Post by jrcullen007 on 2007-04-13
whats should i change them to  
         Section "Monitor"
	Identifier	"benq fp731"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
which should i change and to what

---

### Post by dunedust on 2007-04-13
That would depend on your monitor 
Its usually present in the monitor handbook

Also when you change it through * system - preferences - screen resolution*
make sure you click on the *make default for this compute*r option

---

