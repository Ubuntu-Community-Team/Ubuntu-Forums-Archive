---
title: "Small business server (When?)"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by tymiles on 2007-12-14
I have posted here before and I want to see what people think now. 

My opinion is on the server the one thing that is holding Linux back is the ability to be able to setup simple file and print server domains like Mac OS server or Windows 2003 server. 

As we know with Windows 2003 server you just install it and then follow the wizards to set up AD. Add users and then Windows machines to the domain and boom, you have a pretty scalable not so hard to use single signon set up. 

This is also pretty easy to do with Mac OSX server (Tiger, have not used Leopard yet) The thing that gets me about the Mac Server is that they are using Open Ldap, Cups and Samba to do it. You can add more then one Mac Server to the Workgroup (Domain) and replicate your LDAP entries etc. 

I have a small computer company and when my clients want redundant file and print sharing, Linux is the first thing that comes to mind but in the end I end up using Windows because I can make policies etc. I can add Windows, Mac, Unix and Linux machines to Active Directory without much problem. Plus I can teach a 6 year old how to make user accounts, reset passwords, add users to groups etc. 

Now, I could do this with Novel Edirectory (Using their Small business suite or using Open Enterprise Server) but it would be nice to have an open source set up. Maybe on Ubuntu. I have looked at Xandros, they have made a good try, but their system is not redundant. You only have one copy of the network user database. If the primary server goes down then all our users are offline. (Not good) 

Anyway I know I am rambling but I feel until this happens on the small business (And enterprise level) MS is going to always have that market 100% 

Let me know what you think. Maybe you know of project I don't know of. Maybe Fedora Directory Server with Samba could be the way to go? 

Thanks.

---

### Post by blueridgedog on 2007-12-22
I have setup samba/linux small business systems for over a decade and you are basically right, they need a bid more tweaking and management on the outset than a similar windows product.  They also require a competent sysadmin to setup and manage over the long haul versus your aforementioned 6 year old.

So, it can be done, but it is still a complex process relative to what we think is the ideal.  

What is in the future?  Well, I think that using linux as a terminal server is a faster solution to having a single sign on network in place in a short period of time.  I also think that what you are looking for is an out of the box server type distro that assumes it is targeted at a small business that wants single sign-on with LDAP and wants the server to be a file/print/proxy/nat/mail/web/AD all in one machine.

I think we will get there, but not for some time.

---

### Post by tymiles on 2007-12-28
Thank you for your reply. 

I have been also working with Linux for a long time. I know what I am looking for can be done on Linux using edirectory. But it's cumbersome and edirectory is not open source. 

The best example of what I would love to see on Linux as I have said before is Open Directory on Mac server. It's the closest thing to AD outside of Windows. And it is built on Open Source (Even though they have their own interfaces.) 

[http://en.wikipedia.org/wiki/Apple_Open_Directory](http://en.wikipedia.org/wiki/Apple_Open_Directory)

[http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf](http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf)

[http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html](http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html)

If we had this going on Linux I would be rolling out Linux like it's going out of style. Then I would only need maybe one or two Windows servers as application servers. Not the other way around where now I user Windows servers for AD, then I use Windows servers for Applications (That don't run on Linux and Unix) and I use Linux for Web, Database and Mail servers. 

I would love to use Ubuntu as my core directory and user management servers! I would use Open Directory but it only runs on Mac hardware. :-( 

Anyway if anyone knows anything I don't, please put in your 2 Cent.

---

