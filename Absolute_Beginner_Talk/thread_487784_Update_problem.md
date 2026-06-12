---
title: "Update problem"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-06-29
Hi,
I've got the updates available icon showing.
When I click on it, it says
E: dpkg was interrupted, you must manually run 'dpkg--configure-a
' to correct this problem.

I'm assuming that I enter that code in terminal.
When I do, it says command not found.

So.........what's Plan B?

Phil

---

### Post by paradoxni on 2007-06-29
dpkg --configure -a  

note the spaces

---

### Post by overdrank on 2007-06-29
> **groeswenphil said:**
> Hi,
I've got the updates available icon showing.
When I click on it, it says
E: dpkg was interrupted, you must manually run 'dpkg--configure-a
' to correct this problem.

I'm assuming that I enter that code in terminal.
When I do, it says command not found.

So.........what's Plan B?

Phil

HI IF if you will run the command in the terminal
[PHP]sudo dpkg --configure -a[/PHP]
That should fix the problem. Good Luck!:popcorn:

---

### Post by Seisen on 2007-06-29
Make sure to add sudo in front of it too.

---

### Post by groeswenphil on 2007-06-29
Thanks.

It did this.

Setting up libexchange-storage1.2-1 (1.6.1-0ubuntu7.1) ...

Setting up libecal1.2-3 (1.6.1-0ubuntu7.1) ...

Setting up libebook1.2-5 (1.6.1-0ubuntu7.1) ...

Setting up libedataserverui1.2-6 (1.6.1-0ubuntu7.1) ...

Setting up libedata-book1.2-2 (1.6.1-0ubuntu7.1) ...

Setting up libedata-cal1.2-1 (1.6.1-0ubuntu7.1) ...

Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.



Does that mean its fixed....only the update doesn't appear to be updating.
Thanks,
Phil

---

### Post by Seisen on 2007-06-29
Apparantly it wasn't done installing somethings, after that is done let us know if any errors came up.

---

### Post by groeswenphil on 2007-06-29
Nothing.

I waited and nothing happens.

I press enter ...nothing happens.
I press no and enter and it says that the process was aborted.

What exactly is happening here?

Phil

---

