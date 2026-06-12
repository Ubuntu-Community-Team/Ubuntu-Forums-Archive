---
title: "network setup"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-09-11
i want to share files from ubuntu to windows. i think i have most of this done i see ubuntu on the windows computer but im not to sure what user and password is ive put the ones i use to login to ubuntu and it just sits there. do i need to make a new one on ubuntu for this to work?

---

### Post by hyper_ch on 2007-09-11
well, you are using Samba I suppose... you need to add a user to the samba-user list. The user has to be an existing system user.

```

sudo smbpasswd -a USERNAME

```

---

### Post by trucker33377 on 2007-09-11
no i dont think thats what i used. and i fell pretty dumb right now couse im not sure how i did set it up. i do see all the computers at both ends. from ubuntu and from the other box with windows. i tried to install simba but it wouldnt install

---

### Post by krlill on 2007-09-11
Found this link from an earlier thread .  

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

I was totally lost until i watched this tutorial.  In the comments section  a viewer adds:

"Hi Rich im new to linux and like ubuntu. Problem is i tryed to setup file sharing and it didnt work followe this video several times. The problem is if there is no user setup in user groups in Ubuntu it will not setup a usere for samba. It will work after that. Took lots of reading to find that out. Thanks it now works great jobe just need tweaking for new Os install to work." 

To which rmenga, the tuturial guy, adds:

"What I do to get around that is to make the username for all OS's involved the same, as in the username for login to Windows XP is the same as the Ubuntu username is the same as the Samba username. To be best of my knowledge this works without adding any additional usernames or groups. Thanks for the compliments, much appreciated."

---

### Post by advarntek on 2007-09-11
the tutorila is great watch it and you will never have a problem. its the same if you are using ubuntu 7

---

### Post by krlill on 2007-09-11
I forgot!  It's a good idea to backup smb.conf first.

From an earlier thread, type or copy and paste into Terminal:

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original

---

### Post by trucker33377 on 2007-09-11
i followed the video all the way to making the password it still wont let me do that. and i get the same thing if i use the command from the video also

---

### Post by krlill on 2007-09-11
sudo smbpasswd -a USERNAME

Did you replace -USERNAME- with your login name?   I assume it's lonnie?

---

### Post by trucker33377 on 2007-09-11
ah no i follow dir to the T..... but that worked thxs :))

---

