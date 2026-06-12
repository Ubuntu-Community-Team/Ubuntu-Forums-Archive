---
title: "VMWare  Workstation 5.5.3 permission problem"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by getut on 2007-03-01
I just installed Vmware Workstation 5.5.3 on Edgy and am having a permissions problem. i can run it wth sudo but I followed exactly the same steps I did on my other laptop, but on this one I get the following error from the icon:

Could not launch menu item: Failed to execute child process "vmware" (Permission Denied)

and this error from commandline:

bash: /usr/bin/vmware: Permission Denied

It works fine if I use sudo vmware from the commandline or if I edit the icon to be gksudo vmware. I do not have to do this on my other Edgy laptop.

I've seen various mention of this error in my forum searches but no one got it resolved that I can find.  I uninstalled/reinstalled about 10 times and nothing I have tried has fixed it.

If this were windows I would diagnose by turning on auditing and determine what files I was being denied access to, but I do not have that level of proficiency with Linux yet so I am stumped and am here for help.

---

### Post by getut on 2007-03-01
Ok... I've googled and searched the forums for hours and still no resolution to this. I've found PLENTY of references to the problem, but no one else who has asked seems to have gotten an answer either.

Each time I installed, I took all the defaults with no changes. Like I said it works fine when run with sudo, but run as a standard user and it bombs.](*,) ](*,) ](*,)

---

### Post by sanitycheck on 2007-03-01
I run Workstation 5.5.3 on Edgy amd64 with no problem running it as my regular user.  The various vmware files under /usr/bin are all owned by root, are executable, and Owner/Group/Others are all set to read (I checked properties using Konquerer as a file manager).  

I'd like to mention that after installing regular Kubuntu updates I had to re-run the installation script to get Workstation and Player to work again.  Seems it wasn't happy with the latest kernel update.

---

### Post by getut on 2007-03-01
This is getting more annoying the more I use it.

I've now noticed that when I use Vmware .host sharing... anything I put into linux from the vm'd windows is put in as root. So I can't do anything with it unless I up my privs with sudo or something.

Please help me someone. I've uninstalled and reinstalled and wiped out remaining folders between uninstalling and reinstalling and still when I go back with vmware workstation 5.5.3 and take all defaults, it goes back but will only run with sudo or gksudo.

I don't know how to audit to see what exact file or resource I am being denied access to.

---

### Post by getut on 2007-03-02
Last bump before I give up on it.

I would love help with the problem directly, but if someone could at least point me in the right direction to audit what is wrong like can be done in XP... that may get me going also.

---

### Post by Maestro23 on 2007-03-02
You said you have checked everywhere, but I ran a keyword search over at the Vmware forums for "can only run vmware as root" and got many hits on the subject.  Just a thought, if you haven't already checked there.  If so, disregard.

On your system, who owns [COLOR="Red"]~/.vmware/preferences[/COLOR]
Good luck.

---

### Post by sanitycheck on 2007-03-02
Did you check the permissions of the files I listed in my last post?

When you uninstall the application, many of the files may remain in place.  I don't know this for sure about VMWare Workstation, but it is often true of most applications.  The good reason for leaving some files behind is to keep any settings you had when you first ran the program, in case you might want to use them when you reinstall the program.  

But the bad side of that is you can't uninstall any problems you encounter on the first installation.  So my theory is that you had a problem just during the initial installation, but subsequent uninstall/reinstalls left the problem file or files behind.

Again, checking the permissions of at least some of the main files might shed light on the problem; compare them to what I listed in my earlier post.  To fix a dirty uninstall, uninstall the application again, then do your best to fish around and delete any vmware files that are left behind, then reinstall it in the hopes that everything will be new.  

Hope that helps.

---

### Post by getut on 2007-03-02
Yes.. checked perms on all that I can find and still no change. Reinstalled many times and tried my best to make sure there were no orphan files or folders left after each uninstall. I agree fully about there being SOMETHING out there that I just haven't found yet. I wish I knew how to audit.

I've gotten a response on the vmware forums and am trying to get some help there also. So far nothing has worked.

---

