---
title: "setting up a webserver and can't figure out zoneclient"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-04-26
Bear with me while I work this out...I have set up an account with zoneedit and I am in the process of setting up my zoneclient but I am lost on how to do this.  The instructions online make a lot of assumptions and as such I do not know the following:

Where do I create the file zoneclient.py?
How do I create a python file?
How do I copy everything without having to type the whole script?  apple+c/apple+v is not working when trying to view the script on my mac and copying it to a terminal ssh window.


Also, I am open to any other solutions for updating my cable ip address.  I am using feisty fawn server hence the need for doing this across an ssh client.

Thanks in advance,

Dan

---

### Post by HurricaneDan on 2007-04-30
So I have worked on this over the weekend and it seems that I was able to get it to working with the following:

wget -O - --http-user=username --http-passwd=password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'

I am now going to set it up as a cron job and see if that will keep it updated.

Thanks for those that looked and I hope if anyone else has a similar issue finds this post.

Dan

---

