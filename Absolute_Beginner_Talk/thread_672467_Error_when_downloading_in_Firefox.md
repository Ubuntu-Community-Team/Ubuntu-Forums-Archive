---
title: "Error when downloading in Firefox"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-01-19
When try downloading anything in Firefox, a popup comes up which says

```
XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 4:
     
     var mimeLiteral = gRDF.GetLitertal(aValueString);
_ _ _^
```

Any idea what's wrong?

---

### Post by jeffus_il on 2008-01-19
Have you installed a download extension/plugin, see Tools>Addons

---

### Post by Yes on 2008-01-19
Tools > Addons gives  me this:

```
XML Parsing Error: syntax error
Location: chrome://mozapps/content/extensions/extensions.xul
Line Number 1, Column 1:

box-align: center;
^
```

What's wrong with my Firefox :(

e:  I reinstalled it and now it seems to be working.

---

### Post by jeffus_il on 2008-01-19
Your firefox is very ill.
You could delete the firefox configuration in your home directory, and then reconfigure to your own needs.
In nautilus, change your options to "show hidden files"
change to the .mozilla folder in your home folder and delete the firefox folder.

---

### Post by dan l on 2008-02-05
XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 4:   var mimeLiteral = gRDF.GetLiteral(aValueString);
---^


Same deal.  though:  Clean install.  All I've done is added flash.  What do I do?

---

### Post by FuturePilot on 2008-02-05
Try jeffus_il's suggestion. Close Firefox first though.

---

