---
title: "Cannot access MSHOME form Samba"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by scwinn on 2006-12-18
I see the other computers on the network when I run Samba... I can drill down to their drives but when I try to look at the contents of the dirves I get an authentication screen. My MSHOME network has no need for authentication (home network ... no security is set.) When I try to gain access it says that Samba cannot mount the selected share... or some such thing. Does anyone know what gives??

PS - I love LINUX.... its great!!!

---

### Post by dbbolton on 2006-12-18
i had to enable WINS servers to get samba to work.

---

### Post by scwinn on 2006-12-18
Sorry... I'm a newbie... how do I enable WINS??

Thanks

---

### Post by dbbolton on 2006-12-18
you right-click you network connection, then click properties. in the white box, pick "TCP/IP" and click the properties button. on the window that pops up, click the "Advanced" button near the bottom. then click on the WINS tab, and click "Add WINS Server", and type in the IP address of your router. click ok. then click the radio button that says "Enable netbios over ..." and just click all of the Ok buttons, and reboot.

---

### Post by thelinuxguy on 2006-12-18
> My MSHOME network has no need for authentication (home network ... no security is set.) 

Try this:
1) Add an exception to the windows firewall from Control Panel for the port that Samba Client uses (you will need to dig that out). Or just disable the firewall temporarily to see if it works (Remember to turn it on when u r done).
2) Enable the guest account on Windows with a password. (Control Panel -> User Accounts). Use that to login when prompted.
3) Enable Remote Desktop (although this is required only for remote login) (My Computer -> Properties -> Remote -> Allow users to connect remotely to this computer)

I had to do all three to get it working. You may want to have a look at the "Common Issues" section at [http://gentoo-wiki.com/HOWTO_Setup_Samba]("http://gentoo-wiki.com/HOWTO_Setup_Samba")
(although it is for Gentoo).

Do let us know if this solves your problem.

Regards.

---

### Post by scwinn on 2006-12-18
Sorry.. I'm a real newbie.... but I have to start somewhere... so don't laugh ok... where is Network Connection?? I see something called that running on the bar at the top of the screen, but when I right click there is nothing that sayds "properties"

---

### Post by crane on 2006-12-18
I believe he is taking about you windows box. Click the start menu, then right click Network neiborhood or what ever it is called. Also be sure the windows box is using MShome and not workgroup for the workgroup.

---

### Post by dbbolton on 2006-12-21
yeah i should have said that :)

---

