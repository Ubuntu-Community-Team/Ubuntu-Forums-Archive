---
title: "I would I install this ?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-22
--- usp 2006-07-30 07:08:09.000000000 +0200
+++ usp2 2006-07-30 18:55:05.000000000 +0200
@@ -1114,25 +1113,29 @@


def Filter(self,widget,categorytext):
- self.ShowAllApps()
- self.wTree.get_widget("entry1").grab_focus()
-
- if self.donotfilterapps == False:
- for i in self.wTree.get_widget("vbuttonbox9").get_children( ):
-
- if categorytext == "":
- full_label = i.Label1 + i.Label2 + i.Label3 + i.Label4
+ full_label=text=""
+ showAllAppsBool=False
+ if categorytext != "" or self.donotfilterapps == False:
+ self.ShowAllApps()
+ self.wTree.get_widget("entry1").grab_focus()
+ showAllAppsBool = True
+
+ for i in self.wTree.get_widget("vbuttonbox9").get_children( ):
+ if categorytext != "":
+ showAllAppsBool = True
+ full_label = i.Label3
+ text = categorytext
+ self.wTree.get_widget("entry1").set_text('')
+ else:
+ if self.donotfilterapps == False:
+ full_label = i.Label1 + i.Label2 + i.Label3 + i.Label4
text = self.wTree.get_widget("entry1").get_text()
- else:
- full_label = i.Label3
- text = categorytext
- self.wTree.get_widget("entry1").set_text('')
-
- if not re.search(text,full_label,re.IGNORECASE):
- i.hide()
- else:
- i.show()

+ if showAllAppsBool == True:
+ if not re.search(text,full_label,re.IGNORECASE):
+ i.hide()
+ else:
+ i.show()

def AddFavourite(self,a,widget, event, Exec, ButtonBox,menutogo):
self.Add_Button(widget.MyButtonName,'application', False)
__________________

---

### Post by Tyke91 on 2007-08-22
good rule of thumb... if you don't know what the hell it is... don't install ;)

---

### Post by Nekiruhs on 2007-08-22
Thats a diff file. I assume the source is in python, as thats what the diff file looks like it is. Save the text in ~/diff.patch. Find the relevant source file. Cd into the containing folder and type ```
patch -p0 < ~/diff.patch. Done.
```

---

### Post by swoll1980 on 2007-08-22
Thanks

---

### Post by swoll1980 on 2007-08-22
The source file is a program called  usp2 this is the beta patch for it. How would I find it? I found a usp folder in /usr/share/ it has three files in it dotted.png, usp2.glade, and uspconfig.glade Would this be the folder I'm looking for

---

### Post by swoll1980 on 2007-08-22
command-not-found: error: no such option: -p
bash: -p0: command not found

---

