---
title: "Errors installing SSH server"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by somnathnag on 2006-04-15
Hello :

I am new to Ubuntu / Linux. I could install it - works fine with net and could install the programming packages and other useful stuff.

I am facing problem with installing ssh server.

It does dependency check and in turns talks of installing openssh-server and which in turn talks about openssh-client. While installing openssh-client - I get these errors which I can't understand.

I am new to these stuff so am looking for some help / direction from the community.

I have copied the error as well.

Thanks
Somnath.

root@somnathnag:/usr/bin# apt-get install ssh
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ssh: Depends: openssh-server but it is not going to be installed
E: Broken packages
root@somnathnag:/usr/bin# apt-get install openssh-server
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.1p1-7ubuntu4) but 1:4.1p1-7ubuntu4.1 is to be installed
E: Broken packages
root@somnathnag:/usr/bin# apt-get install openssh-client
Reading package lists... Done
Building dependency tree... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
root@somnathnag:/usr/bin#

---

### Post by munga_bill on 2006-04-15
Hi, somnathnag, have you tried opening synaptic package manager and clicking on 'Edit', and then 'Fix broken Packages' from the drop-down menu?
Maybe you already tried that? Just trying to be helpful...Regards, munga_bill

---

### Post by munga_bill on 2006-04-15
Sorry for the double-post - (some kind of internet error).

---

### Post by steve.horsley on 2006-04-15
I believe the SSH clisnt is installed by default. Try just this:
**sudo apt-get install ssh-server**
It's been a while since I installed SSH myself, and I vaguely remember some odd messages about compatibility, but I think just installing ssh-server should work OK.

---

