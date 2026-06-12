---
title: "kde update on ubuntu ??"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-06-01
hi all i just saw that there are some new updates for ubuntu ! 

well .... as the packages are pretty big i wanted to know what they are for ...and : 

kdelibs.bin
kdelibs.data
kdelibs4

well for what do i need these packages exactly ? ( i mean are they installed from ubuntu itself ? i know that they are needed to run kde applications ( its just that i cannot remember, that i have installed these packages ! ) nor am i sure if i am running a kde application at all ! )

if i don want to install these packages .. can you tell me how i can remove them from the updates? cause right now there is always the red circle in the toolbar ;) which is  a little annoying ;) 

thanks for any info !

---

### Post by Mez on 2005-06-01
Open up synaptic, and then click on "search"

in the box, search for "kdelibs4" without the quote

now.... click on kdelibs4, and click "mark for removal"

this will then pop up a box telling you what the kdelibs4 is needed for, and whether you want to remove these aswell.

If you see anything in that lsit that you want to keep, then I suggest you update to the latest versions.

If you dont see anything in that list that you want, It's safe to remove them, however, you may find that something you installed is no longer available!

Hope this info Helps!

---

### Post by hiptrop on 2005-06-01
thansk alot :) seems like i have installed it for k3b ! 

all i wanted to know ;)

---

### Post by heart_reaver on 2005-06-02
hi there your downlaod problem can be solved by using wget commnad in terminal

example of command :


$ wget -c url_of_file_to_be_download

by using -c in wget command you can continue your download if any anything go bad with network.


also see gwget at google it is gui for wget



heart_reaver

---

### Post by stevenyu on 2005-06-02
The quickest way will be using the **apt-get** command in terminal window

**# sudo apt-get update**

and

**#sudo apt-get upgrade**

---

