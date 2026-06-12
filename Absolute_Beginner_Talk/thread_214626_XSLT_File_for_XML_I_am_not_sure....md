---
title: "XSLT File for XML?? I am not sure..."
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by kranknut on 2006-07-12
Hi,
I am trying to use Tellico and import an XML file in it. When I do this it asks for a XSLT file; exact quote, "A valid XSLT file is needed to import this file." Through Synaptic I then tried to find XSLT Utilities. The gnome-doc-utils was already loaded. And then I loaded Sablotron [The description said "Sablotron is a fast, compact and portable XML toolkit implementing XSLT 1.0, DOM Level2 and XPath 1.0."]. It hasn't seemed to help...in fact I can't even figure out where Sablotron is? I checked the installed files and this is what came up:
/usr/share/doc
/usr/share/doc/libsablot0
/usr/share/doc/libsablot0/README
/usr/share/doc/libsablot0/copyright
/usr/share/doc/libsablot0/changelog.Debian.gz
/usr/lib
/usr/lib/libsablot.so.0.100.2
/usr/lib/libsablot.so.0
I don't think any of them is the "exec" file (yes I am tainted with a Windows background).

Can anyone please help??
Thanks...

---

### Post by parys on 2006-07-19
What kind of XML file are you trying to import? The XSLT file should convert your type of XML to the Tellico XML format.

---

### Post by mattisking on 2006-07-19
An XSLT is generally used to convert an XML file into "another file". It can be used to extract a webpage from an XML file retrieved via a web service. It can be used to convert one XML layout into another. I'm not familiar with Tellico (or KDE for that matter) but it sounds like you might be using it wrong... or for whatever reason, Tellico doesn't know what to make of the XML file you are giving it and is looking for instructions.

---

