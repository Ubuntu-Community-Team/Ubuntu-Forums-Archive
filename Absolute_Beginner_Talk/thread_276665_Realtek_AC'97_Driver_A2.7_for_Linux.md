---
title: "Realtek AC'97 Driver A2.7 for Linux"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-10-13
Ok, I've got an Asus K8N SLI Deluxe mainboard. I want to innstall the sound drivers for the built in soundcard. When I download it, it seems like I have to compile the source myself, and a whole lot more.

LINK:
[http://support.asus.com/download/download.aspx?SLanguage=en-no](http://support.asus.com/download/download.aspx?SLanguage=en-no)
You will find the drivers there.





BTW: I know I registred my account a _long_ time ago, but I onlys use Linux now and then. So I've started up again, and every time I get one step further. This time I think I've realy made it, but the crappy sound ain't no fun.

---

### Post by d4rk on 2006-10-13
*bump*
Ok, I regret that bump.

---

### Post by Sef on 2006-10-13
> When I download it, it seems like I have to compile the source myself, 

To compile, you need build-essential.

Open the terminal. (Applications > Accessories > Terminal)

sudo aptitude update

sudo aptitude install build-essential

---

### Post by d4rk on 2006-10-14
Ok, I ran those commands in terminal, and it executed successfully.
Now what? The drivers I downloaded exists of like hundreds of files...

OK, Isn't Ubuntu kind of useless when I'm not able to play off music in it without having such a bad quality? When I used Win I realy didn't have to compile my drivers. I just double-clicked at an icon, and it worked perfectly.

---

### Post by Sef on 2006-10-14
> Ok, I ran those commands in terminal, and it executed successfully.
Now what? The drivers I downloaded exists of like hundreds of files...

Check out this site on how to install from source: [How to Install Anything.]("http://monkeyblog.org/ubuntu/installing/#installing_with_terminal") (Go down to install from source.)

---

### Post by d4rk on 2006-10-14
Did that, but it didnt't work. The sound is still crappy, and several errors occured under innstallation. Never knew it was so hard to innstall some sound drivers...

BTW, I must mention 1 thing, in the beginning the sound was quite Ok, but suddenly a day or two ago it all went to hell with it. Could anyone tell me how to check if the drivers is installed?

---

### Post by jimmygoon on 2006-10-14
> **d4rk said:**
> Did that, but it didnt't work. The sound is still crappy, and several errors occured under innstallation. Never knew it was so hard to innstall some sound drivers...

BTW, I must mention 1 thing, in the beginning the sound was quite Ok, but suddenly a day or two ago it all went to hell with it. Could anyone tell me how to check if the drivers is installed?

Er... this is the most popular sound card in laptops... I have it, so do ALL of my friends... ubuntu supports it out-of-box (every distro does) and the fact that it HAD been working.... makes it very easily for me to say "user error"...

---

### Post by d4rk on 2006-10-16
> **jimmygoon said:**
> Er... this is the most popular sound card in laptops... I have it, so do ALL of my friends... ubuntu supports it out-of-box (every distro does) and the fact that it HAD been working.... makes it very easily for me to say "user error"...

Ok. It happened after that i installed a whole lot of crap from Automatix i think. How can i "reset" the system ?

---

### Post by PriceChild on 2006-10-16
Yup i'm on a nice GA-7VAXP and AC97 is perfect.

I don't like automatix as it crashes pretty badly. - much better to learn how to do everything yourself.

---

