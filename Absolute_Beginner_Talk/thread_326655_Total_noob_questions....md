---
title: "Total noob questions..."
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2006-12-27
I just installed ununtu 6.06. I have my box connected directly to my cable modem ( I have comcast cable). My goal is to used this box as a server. I used System => Synaptic Package Manager to (hopfully) install apache2, php5, and Mysql. Although I did not install Mysql directly, like apache2 and php5.

I would like to know how do I go about seeing if I have mysql and perl5 installed?

I want to install webmin to configure my server. However, when the package installer runs webmin I get the error message: Dependency is not satistfiable: libauthen-pam-perl??? I don't know what that means.

Thanks in advance for the help

---

### Post by po0f on 2006-12-28
cap10kirk,

Have you tried installing [libauthen-pam-perl](http://packages.ubuntu.com/dapper/perl/libauthen-pam-perl)?  It's in the repos; a search through Synaptic would have revealed this.

Are you sure you want to run a web server?  I'm not bashing you or anything, but installing software and satisfying package dependencies are pretty trivial stuff compared to being a web admin.

---

### Post by cap10kirk on 2006-12-28
> **po0f said:**
> cap10kirk,

Have you tried installing [libauthen-pam-perl](http://packages.ubuntu.com/dapper/perl/libauthen-pam-perl)?  It's in the repos; a search through Synaptic would have revealed this.

Are you sure you want to run a web server?  I'm not bashing you or anything, but installing software and satisfying package dependencies are pretty trivial stuff compared to being a web admin.

There is nothing to it, but to do it.:p I actually got my server up and running where it shows the apache splash page. but i have a lot of questions. but i'll hold off in the morning.

kirk, out.

---

### Post by 3rdalbum on 2006-12-28
Ubuntu isn't really an appropriate Linux distro for Webmin. Webmin requires the creation of a real root account, which you can do on Ubuntu, but it's a little bit more work.

---

### Post by TopKnot1 on 2007-02-23
> **po0f said:**
> cap10kirk,

Have you tried installing [libauthen-pam-perl](http://packages.ubuntu.com/dapper/perl/libauthen-pam-perl)?  It's in the repos; a search through Synaptic would have revealed this.

Are you sure you want to run a web server?  I'm not bashing you or anything, but installing software and satisfying package dependencies are pretty trivial stuff compared to being a web admin.

You know...I've been trying off and on for two days to install webmin.  I've read about 30 billion posts about the probem with libauther-pam-perl and then I come upon this little remark above.  

The search function in Synaptic really works if you know it exists.  In the 5 minutes it took me to read, understand and then do the install of this dependency file you gave instructions for, all my frustrations with learning Ububtu were erased.  5 minutes after installing that file I had webmin installed.

Thanks for this most awesome post!  I'll get through this new operating system learning curve if it kills me.

Thanks again

---

