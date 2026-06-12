---
title: "environment variable"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by dcollier on 2008-02-05
I am trying to install NET FRAMEWORK 3.0, but to get it working I need to set the value below in the environ variable.  I don't know where to configure this file.  I got this entry from the wine bug 9158.  Help :( 

export _SFX_CAB_SHUTDOWN_REQUEST=some_value

Set this environ variable before starting the installer. The special file will
be skipped then in the copy process.

---

### Post by emarkd on 2008-02-05
Not sure about that .net stuff, but you can set a variable in your current session environment just like you typed it here.  Go to the terminal and type just what you've got there.  If you want to make sure it worked, you can do 'echo $variablename'

---

### Post by kerry_s on 2008-02-05
> **dcollier said:**
> I am trying to install NET FRAMEWORK 3.0, but to get it working I need to set the value below in the environ variable.  I don't know where to configure this file.  I got this entry from the wine bug 9158.  Help :( 

export _SFX_CAB_SHUTDOWN_REQUEST=some_value

Set this environ variable before starting the installer. The special file will
be skipped then in the copy process.

sudo gedit /etc/environment
drop the export
example:
SFX_CAB_SHUTDOWN_REQUEST="some_value"

---

