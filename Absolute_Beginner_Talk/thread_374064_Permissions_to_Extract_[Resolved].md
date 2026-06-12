---
title: "Permissions to Extract [Resolved]"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by leatherworker on 2007-03-02
Hi!

I have searched all over for a solution  - no luck!  Please help!

I am installing Simple Invoices on my Ubuntu Edgy system.

I already have Apache, MySQL, and php installed.  Now I get the following instruction:
[I][INDENT][B][I]"# Now the required software has been installed and is running, download the latest Simple Invoices package from htt://simpleinvoices.sf.net
# Extract the contents of the simple_invoices_yyyymmdd.zip to a simpleinvoices folder in your web servers document root (ie. /var/www in Debian) [/I][/B][/INDENT][/I]

I have downloaded it to /home/myself/downloads    ---  it is a .zip file

I open the Archive Manager and when I want to extract the contained folder 'n contents to /var/www I simply get told that it is a root owned folder and I cannot extract there.

:confused: 

This is where I am stuck.

JOhan

---

### Post by aysiu on 2007-03-02
Extract it to your own directory (/home/myself/downloads) with the Archive Manager.

Then press Alt-F2 and type ```
gksudo nautilus
``` This will open the file manager with root permissions. You can then drag the extracted folder from /home/myself/downloads to /var/www

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by leatherworker on 2007-03-02
Thank you so much,  aysiu.  That worked exactly and adds to my own stash of knowledge!  And thanks for the great work you guys are doing on these forums!

---

