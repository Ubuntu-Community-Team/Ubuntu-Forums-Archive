---
title: "Java on Lombard Powerbook G3"
date: 2005-04-03
forum: Apple PPC Users
---

### Post by guinness on 2005-04-03
Hi,

How do I get a Java plugin for Firefox to work on my Lombard? Have installed Ubuntu and all's well so far except that I can't seem to find a Java plugin for Linux/POWERPCs? Do I use the version off the Mac site for Mac OS X? If so, how do I go about doing that? Thanks!

I just need the plugin, not doing any hardcore Java stuff on this trusty old Lombard :)

---

### Post by prio on 2005-04-04
No java plugin for mozilla on linux ppc I'm afriad. If you need java support you are going to have to use konqueror or opera. 

Downloading the IBM JRE binaries is a three step process.

1. Go to [https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p) and select “IBM SDK for 32-bit iSeries/pSeries, 1.4.2 GA 2&#8243;. Press the button labeled “Continue".

2. If you have an account at IBM DeveloperWorks already log in, otherwise you will have to register (it is free).

3. Find the “Java Runtime Environment"-section on the download page and press the “Accept License” button next to: “tgz format: IBMJava2-JRE-142.ppc.tgz 41.5MB". Do the same thing for “Java Communications API” on the same page. Get the tgz version, not the RPM (that is for YellowDog GNU/Linux).

The next thing to do is to unpack the binaries in a suitable location. Open up a terminal window and type “su -", then enter the password of the “root” user account. It is also possible to install the Java Runtime Environment in your home directory, but then you will be the only user on the system that can utilise it.

Go into the “/opt” directory by typing “cd /opt". Unpack the two files you have downloaded by typing “tar zxfv /path/to/file/IBMJava2-JRE-142.ppc.tgz” and “tar zxfv /path/to/file/IBMJava2-JAVACOMM-142.ppc.tgz", replace “/path/to/file” with the actual filesystem path to the downloaded file (for instance “/home/johndoe"). You can now close the terminal window.

Opera:

To set up Opera to use Java press “Tools” in the menu bar and select “Preferences". A new window will pop up, select “Multimedia". Make sure the “Enable Java” check box has been enabled and enter “/opt/IBMJava2-ppc-142/jre/bin” in the “Java path:” text box. Press OK when you are done.

Konqueror:

Select “Settings” from the menu bar and click “Configure Konqueror". Press the “Java & JavaScript” buttom. Make sure the “Enable Java globally” check box is enabled and enter “/opt/IBMJava2-ppc-142/jre/bin/java” in the “Path to Java executable, or ‘java’:” text box. Press OK when done.

Hope that helps.

---

### Post by trash on 2005-04-10
Excellent howto prio!

I'm having trouble locating the "IBMJava2-JRE-142.ppc.tgz 41.5MB" which doesn't appear on the link provided.... I know i can search the IBM site but i'm wondering if i really need it at all?

In warty we only needed the SDK and the 'java virtual dummy' package from debian repos. Is this a no go in Hoary?

EDIT: this is all to get Mercury installed and running, which i'm not even sure yet if its possible yet... [http://www.mercury.to/index.php](http://www.mercury.to/index.php)
anybody tried it yet?

---

### Post by prio on 2005-04-11
[QUOTE=trash]Excellent howto prio!
In warty we only needed the SDK and the 'java virtual dummy' package from debian repos. Is this a no go in Hoary?
[/QUOTE]
Not a debian/ubuntu user for long so didn't know about that method. Give it a try and let me know how you get on.

---

