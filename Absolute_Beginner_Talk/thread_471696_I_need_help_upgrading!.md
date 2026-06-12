---
title: "I need help upgrading!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-12
Ok, i have given up on downloading and installing feisty from the internet. I have reqested a cd but god knows how long that will take to reach me. I have tried downloading the .ISO from  several mirrors, i used winMD5sum to check the validity of the .ISO, tried burning the valid iso on 2 different cd burners at 1x speed, but whenever i check the disc for errors i get a message saying "invalid or corrupt kernel image." So the route i am taking is installing a really old version (5.04 to be exact) and manually upgrading.

I guess the question in am asking is...how do i do this.  I have tried to go through the GUI update manager and it says that my system is up to date(5.04?) Then i tried to go through the terminal and i typed-->  
gksu “update-manager -c ”
(which i believed to do the trick)
and it prompts me for a password then gives me an error message.

I am at work right now and my linux box is at home so i cant relay the exact message i was receiving because i just couldnt remember it.  Is the way i am going about this correct? Is there a better way? PLEASE HELP!

---

### Post by starcraft.man on 2007-06-12
Ok, I'm gonna advise you against that move. To upgrade all the way to Feisty your gonna have to go through each and every update in between, meaning:

5.04 > 5.10 > 6.06 > 6.10 > 7.04

Just doesn't seem worth it to me, lots of time and bandwidth wasted. Can you try downloading Edgy [from here ]("http://releases.ubuntu.com/6.10/")and giving that a shot? [Follow this for burning ]("https://help.ubuntu.com/community/BurningIsoHowto")and if it does go successful the upgrade from there should be an easy one step upgrade.

I'm not sue why your burns failed so much. What software were you using on windows? Have you tried another burner? Maybe its failing... and its time for a new one?

Oh and the ship it CDs don't usually take too long, less than 2 weeks is standard I believe.

---

### Post by ITdrummer on 2007-06-12
> **starcraft.man said:**
> Ok, I'm gonna advise you against that move. To upgrade all the way to Feisty your gonna have to go through each and every update in between, meaning:

5.04 > 5.10 > 6.06 > 6.10 > 7.04

I understand, i was just frustrated that i have made about 6 coasters out of failed downloads/burns lol


> **starcraft.man said:**
> I'm not sue why your burns failed so much. What software were you using on windows? Have you tried another burner? Maybe its failing... and its time for a new one?


I used nero premium the first time, then i used the free burning software recommended on the ubuntu website, InfraRecorder.  My burners are fine(i assume) because i have no problem burning anything else. Actually the first burner i used is brand new. I will try downloading edgy and proceeding from there. Thanks

---

