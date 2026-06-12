---
title: "What a mess...Boot up help please"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-06
Hi all,

Trying to help a friend out of a jam. Here the scenario - He installed Feisty and it worked fine except for their DSL internet. They couldn't seem to get connected.  Now I don't know how much they tried of if they were even aware of these forums but I wasn't called untill after the mess.  So they call the ISP and wouldn't you know it they said that they do not have support for *nix. The ISP told them that they would have to have Windoze. So the next thing he did was installed xp over ubuntu. Now they call me...The system will not boot it freezes and theysaid you cant even get into the system bios.

If I just disconnect the HDD do you think that will free up the bios?  I want to reinstall Ubuntu...any ideas?

---

### Post by PmDematagoda on 2007-10-06
It would be worth a try, though I don't think the HDD would be damaged due to formatting, it would mostly be something with the mainboard or something related to the BIOS to stop the BIOS from showing.

---

### Post by mramsey on 2007-10-06
I wondered if there might still be some element of grub on there and it was getting confused.  I also have a clean HDD I can throw in there.  My hope is that I can just disconnect the existing HDD and manage to free up the bois. Then set to boot from the CD. Can I reformat with gparted or should I just let ubuntu do it?

---

### Post by PmDematagoda on 2007-10-06
You mean the old HDD? If the problem is indeed caused by the HDD(Very unusual if it is), then it will be very difficult to do anything if you can't even start the computer properly when you use it.

---

### Post by mramsey on 2007-10-06
> **PmDematagoda said:**
> You mean the old HDD? If the problem is indeed caused by the HDD(Very unusual if it is), then it will be very difficult to do anything if you can't even start the computer properly when you use it.


Yes I agree it is unusual.  I will check out his system this afternoon and see for myself. I will post the outcome later.

---

### Post by mramsey on 2007-10-06
Well, got  it going.  I disconnected the HDD, went into the bios and set to boot from CD. I used the Alternate Fiesty Install CD and we are back in business.   He was using a dsl modem wit no router and was having no luck connecting to the internet.  solved that by using```
 pppoeconf
``` to configure the connection.

All is good now!:popcorn:

---

