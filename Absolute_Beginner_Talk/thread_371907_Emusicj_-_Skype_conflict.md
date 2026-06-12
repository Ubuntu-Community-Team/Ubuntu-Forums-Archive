---
title: "Emusicj - Skype conflict?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by whiskyprajer on 2007-02-27
Does anyone know if there is a conflict between Skype and Emusicj?  I've been using the latter for eMusic for the last six months without any trouble whatsoever.  Last week I installed Skype, and now Emusicj is "stuttering" - sometimes it works, most times it doesn't.  I've tried opening it in a terminal, then downloading a song.  When it doesn't work, this is the message I get:

Exception in thread "Server Thread" gnu.xml.dom.ls.DomLSException:
premature end of file (found "[EOF]")
  at gnu.xml.dom.ls.DomLSParser.doParse(libgcj.so.7)
  at gnu.xml.dom.ls.DomLSParser.parse(libgcj.so.7)
  at gnu.xml.dom.DomDocumentBuilder.parse(libgcj.so.7)
  at nz.net.kallisti.emusicj.metafiles.EMPMetafile.<init>(EMPMetafile.java:70)
  at nz.net.kallisti.emusicj.metafiles.MetafileLoader.load(MetafileLoader.java:59)
  at nz.net.kallisti.emusicj.controller.EMusicController.loadMetafile(EMusicController.java:171)
  at nz.net.kallisti.emusicj.ipc.IPCServerClient$ServerThread.run(IPCServerClient.java:197)
Caused by: org.xml.sax.SAXParseException: premature end of file (found "[EOF]")
  at gnu.xml.aelfred2.SAXDriver.fatal(libgcj.so.7)
  at gnu.xml.aelfred2.XmlParser.error(libgcj.so.7)
  at gnu.xml.aelfred2.XmlParser.parseDocument(libgcj.so.7)
  at gnu.xml.aelfred2.XmlParser.doParse(libgcj.so.7)
  at gnu.xml.aelfred2.SAXDriver.parse(libgcj.so.7)
  at gnu.xml.aelfred2.XmlReader.parse(libgcj.so.7)
  at gnu.xml.dom.ls.DomLSParser.doParse(libgcj.so.7)
  ...6 more

If necessary, I don't mind losing Skype.  But I'd hate to lose eMusic.  Any questions/suggestions, etc. are appreciated.

---

### Post by mr_niceguy on 2007-02-27
Looking at the error trace you see a whole lot of classes stemming from "gnu", as in:

gnu.xml.(etc)

instead of Sun Java's usual:

javax.xml.(etc)

I wonder if your Java settings have been reset to use the (crappy) GNU Classpath version of Java?

If you have the Multiverse repository enabled in Synaptic you can install Sun Java. I believe "sun-java5-jre" is probably the one you want. If it is already installed I know there is a command line setting to tell your environment to use it by default but I'm forgetting it off the top of my head. It's in these here forums somewhere as everyone who uses Java gets sick of Classpath eventually.

---

### Post by mr_niceguy on 2007-02-27
> **mr_niceguy said:**
> If it is already installed I know there is a command line setting to tell your environment to use it by default but I'm forgetting it off the top of my head.

A search refreshed the memory... The command is:

sudo update-alternatives --config java

You should see your choices listed 1, 2, etc. You want the highest numbered one with 'sun' in the name. e.g.

```

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
+        3    /usr/lib/jvm/java-gcj/jre/bin/java

```

Here you would want to choose number '1'.

---

### Post by whiskyprajer on 2007-02-28
Brilliant!  That's done it quite nicely, thank you.  Someone buy Mr. N. a cuppa joe!

---

