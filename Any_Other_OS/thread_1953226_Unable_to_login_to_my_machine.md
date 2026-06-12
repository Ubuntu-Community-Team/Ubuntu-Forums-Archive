---
title: "Unable to login to my machine"
date: 2012-04-05
forum: Any Other OS
---

### Post by rmcellig on 2012-04-05
I have a separate partition for my Home directory. I am using Mint 12. I went to install Fuduntu to my sda5 partition. I did something when I tried to point this installation to my /Home directory because when I rebooted into my Mint 12 partition, I keep getting returned to my login screen. I know that my password is OK so I think this may be a permissions issue or maybe my Home partition was moved to another partition after I deleted the Fubuntu after installing it.

I am able to get into a Virtual Desktop when I try to login to Mint 12. My login/password works fine, but I get a permission denied error when I try to access my Home directory. What should I do?

I am still a newbie to all of this so I look at this as a great learning experience!!

Thanks!!

---

### Post by grahammechanical on 2012-04-05
This is a complete and utter guess.

You had two Linux operating systems both using the /home partition. Now, I ask myself, where are the login details stored, such as user name and password. And I am thinking that they are stored in /home under the username.

So, I wonder, is Mint looking in the home folder that Fuduntu set up when it should be looking in the home folder that was set up by MInt?

It clearly is not finding the right folder/file that records your user name and password. I am not familiar with either of these two operating systems. I cannot help more than this.

Regards.

---

### Post by Perfect Storm on 2012-04-06
Moved to Other OS/Distro Talk.

---

### Post by rmcellig on 2012-04-06
> **grahammechanical said:**
> This is a complete and utter guess.

You had two Linux operating systems both using the /home partition. Now, I ask myself, where are the login details stored, such as user name and password. And I am thinking that they are stored in /home under the username.

So, I wonder, is Mint looking in the home folder that Fuduntu set up when it should be looking in the home folder that was set up by MInt?

It clearly is not finding the right folder/file that records your user name and password. I am not familiar with either of these two operating systems. I cannot help more than this.

Regards.

That makes sense to me. But what do I know. I'm still a newbie learning how this all works.

My main concern is that I need to fix this and hope that someone will post a solution for me.

Thanks!!!!

---

