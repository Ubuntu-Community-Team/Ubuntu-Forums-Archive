---
title: "updating 910/915 driver"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by bedake on 2007-03-08
I'm trying to update the driver for this graphics chip set: 

 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

I go to the site to download the drivers here []("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

I'm not so sure where to go from there, I downloaded the tar.gz and tried running the script but it didnt do anything at all for some reason

---

### Post by teaker1s on 2007-03-10
firstly install 
```
sudo apt-get install build-essential
```

scripts must be made executable, either by clicking on properties and ticking the box or in terminal
cd to directory
chmod 755 nameofile.extension

---

### Post by bedake on 2007-03-10
Thanks for the response, when I check it to be exectuable and try to run it the script still doesnt work.  it will open up a terminal briefly and then close it immediately

---

