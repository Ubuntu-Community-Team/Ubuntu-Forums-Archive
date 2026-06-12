---
title: "aMSN is broke"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ketzerei on 2007-10-30
aMSN works on my other GUTSY install, but I tried installing it about 5 minutes ago and get this error:

Error in startup script: bad pad value "2m": must be positive screen distance
while executing
"grid $w.bitmap $w.msg -in $w.top -sticky news -padx 2m -pady 2m"
(procedure "tk::MessageBox" line 182)
invoked from within
"tk::MessageBox -message {The requested file has not been translated into the current language yet.} -type ok -icon info -title aMSN -parent ."
("eval" body line 1)
invoked from within
"eval tk::MessageBox $args"
(procedure "tk_messageBox" line 2)
invoked from within
"tk_messageBox -message "$message" -type $type -icon $icon -title $title -parent $parent"
(procedure "::amsn::messageBox" line 10)
invoked from within
"::amsn::messageBox $msg ok $icon [trans title]"
(procedure "::amsn::infoMsg" line 2)
invoked from within
"::amsn::infoMsg "$msg" "
(procedure "msg_box" line 1)
invoked from within
"msg_box "[trans transnotexists]""
(procedure "::amsn::aboutWindow" line 16)
invoked from within
"::amsn::aboutWindow"
invoked from within
"if {$version != [::config::getGlobalKey last_client_version]} {
::amsn::aboutWindow
catch {file delete [file join $HOME2 bugreport.amsn]}
#Fo..."
(file "/usr/bin/amsn" line 309)

Any ideas?

---

### Post by ketzerei on 2007-10-31
It seems to have mysteriously fixed itself... anyway.

---

### Post by -grubby on 2007-10-31
see if it breaks again

---

