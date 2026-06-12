---
title: "changing mime type  .jnlp files"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-12-24
I am trying to change the MIME types for .jnlp files for my java installation. I installed java by downloading the .bin file from java.sun.com. 

The .jnlp file should be associated with javaws as a Java Web Start application. I used the tutorial here to try and do it :

[http://www.blogmanno.com/?q=node/66](http://www.blogmanno.com/?q=node/66)

This is the .xml file I put in the /usr/share/mime/packages directory:

<?xml version="1.0"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
	<mime-type type="application/java-archive">
		<comment>Java Archive</comment>
		<glob pattern="*.jar"/>
	</mime-type>

	<mime-type type="application/x-java-jnlp-file">
		<comment>Java Web Start application</comment>
		<glob pattern="*.jnlp"/>
	</mime-type>
</mime-info>

I named the file java6u3 since thats the package name I created to install the contents of the downloaded .bin file. 

In /usr/lib/mime/packages i created  java6u3 and used this contents:

application/x-java-jnlp-file; /usr/lib/Java6u3/jre/javaws -viewer %s

I used the commands update-mime and update-mime /usr/share/mime to ensure the new mime types are read. However .jnlp still opens with firefox. 

Any ideas of how to fix this?

---

### Post by blueridgedog on 2007-12-24
How about editing /etc/mime.types and adding a line for application/x-java-jnlp-file?

---

### Post by blueridgedog on 2007-12-24
I think the steps here:

[http://adrianus.wordpress.com/2007/02/07/howto-add-new-mime-types-and-icon-for-visio-document-in-ubuntu/](http://adrianus.wordpress.com/2007/02/07/howto-add-new-mime-types-and-icon-for-visio-document-in-ubuntu/)

are a bit clearer (at least to me).

---

### Post by noorez on 2007-12-25
Here is the new result after following that:

I double-click on a .jnlp file. Firefox opens with it.
The firefox open/save dialog comes up. This time firefox asks to open with the proper program (javaws).

How can I get it so that firefox does not open, rather the program (javaws).

---

### Post by noorez on 2007-12-28
Ok. I added a .desktop entry to /usr/share/applications and it seems to work now. But now I have this problem. If I use this command for Exec=/usr/lib/Java6u3/bin/javaws -viewer,
I can launch java webstart from the Applications menu, but a jnlp won't launch if I double click it. If I leave -viewer, the Java Web Start won't start from the menu but I can double click a .jnlp file to start the program. Is there a way around this problem ?

---

### Post by blueridgedog on 2007-12-28
Could you make two entries, one with viewer and one without (a near random guess).

---

