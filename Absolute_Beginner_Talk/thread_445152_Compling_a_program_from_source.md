---
title: "Compling a program from source"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-05-15
I'm trying to compile a program from source, but I'm having some problems (likely a dependency issue). When I do the "make" command I get this:

```
rutter@stumpy:~/springlobby/trunk$ make
make  all-recursive
make[1]: Entering directory `/home/rutter/springlobby/trunk'
Making all in src
make[2]: Entering directory `/home/rutter/springlobby/trunk/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DwxUSE_GUI=0 -pthread -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2      -g -O2 -MT mainwindow.o -MD -MP -MF .deps/mainwindow.Tpo -c -o mainwindow.o mainwindow.cpp
chatpanel.h:46: error: expected class-name before ‘{’ token
chatpanel.h:69: error: ‘wxCommandEvent’ has not been declared
chatpanel.h:75: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
chatpanel.h:75: error: expected ‘;’ before ‘*’ token
chatpanel.h:76: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
chatpanel.h:76: error: expected ‘;’ before ‘*’ token
chatpanel.h:77: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
chatpanel.h:77: error: expected ‘;’ before ‘*’ token
chatpanel.h:78: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
chatpanel.h:78: error: expected ‘;’ before ‘*’ token
chatpanel.h:80: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
chatpanel.h:80: error: expected ‘;’ before ‘*’ token
chatpanel.h:81: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
chatpanel.h:81: error: expected ‘;’ before ‘*’ token
chatpanel.h:83: error: ISO C++ forbids declaration of ‘wxButton’ with no type
chatpanel.h:83: error: expected ‘;’ before ‘*’ token
mainchattab.h:33: error: expected class-name before ‘{’ token
mainchattab.h:45: error: ISO C++ forbids declaration of ‘wxNotebook’ with no type
mainchattab.h:45: error: expected ‘;’ before ‘*’ token
mainchattab.h:46: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
mainchattab.h:46: error: expected ‘;’ before ‘*’ token
mainwindow.h:35: error: invalid use of undefined type ‘struct wxFrame’
/usr/include/wx-2.8/wx/utils.h:50: error: forward declaration of ‘struct wxFrame’
mainwindow.h:46: error: ISO C++ forbids declaration of ‘wxBoxSizer’ with no type
mainwindow.h:46: error: expected ‘;’ before ‘*’ token
mainwindow.h:47: error: ISO C++ forbids declaration of ‘wxListbook’ with no type
mainwindow.h:47: error: expected ‘;’ before ‘*’ token
mainwindow.h:48: error: ISO C++ forbids declaration of ‘wxNotebookPage’ with no type
mainwindow.h:48: error: expected ‘;’ before ‘*’ token
mainwindow.h:52: error: ISO C++ forbids declaration of ‘wxImageList’ with no type
mainwindow.h:52: error: expected ‘;’ before ‘*’ token
springlobbyapp.h:64: error: ‘wxTimerEvent’ has not been declared
springlobbyapp.h:106: error: ISO C++ forbids declaration of ‘wxTimer’ with no type
springlobbyapp.h:106: error: expected ‘;’ before ‘*’ token
mainwindow.cpp: In constructor ‘MainWindow::MainWindow()’:
mainwindow.cpp:27: error: type ‘wxFrame’ is not a direct base of ‘MainWindow’
mainwindow.cpp:28: error: ‘wxPoint’ was not declared in this scope
mainwindow.cpp:28: error: ‘wxSize’ was not declared in this scope
mainwindow.cpp:31: error: ‘wxMenu’ was not declared in this scope
mainwindow.cpp:31: error: ‘menuFile’ was not declared in this scope
mainwindow.cpp:31: error: expected type-specifier before ‘wxMenu’
mainwindow.cpp:31: error: expected `;' before ‘wxMenu’
mainwindow.cpp:37: error: ‘menuEdit’ was not declared in this scope
mainwindow.cpp:37: error: expected type-specifier before ‘wxMenu’
mainwindow.cpp:37: error: expected `;' before ‘wxMenu’
mainwindow.cpp:39: error: ‘menuTools’ was not declared in this scope
mainwindow.cpp:39: error: expected type-specifier before ‘wxMenu’
mainwindow.cpp:39: error: expected `;' before ‘wxMenu’
mainwindow.cpp:41: error: ‘menuHelp’ was not declared in this scope
mainwindow.cpp:41: error: expected type-specifier before ‘wxMenu’
mainwindow.cpp:41: error: expected `;' before ‘wxMenu’
mainwindow.cpp:44: error: ‘wxMenuBar’ was not declared in this scope
mainwindow.cpp:44: error: ‘menubar’ was not declared in this scope
mainwindow.cpp:44: error: expected type-specifier before ‘wxMenuBar’
mainwindow.cpp:44: error: expected `;' before ‘wxMenuBar’
mainwindow.cpp:49: error: ‘SetMenuBar’ was not declared in this scope
mainwindow.cpp:51: error: ‘m_main_sizer’ was not declared in this scope
mainwindow.cpp:51: error: expected type-specifier before ‘wxBoxSizer’
mainwindow.cpp:51: error: expected `;' before ‘wxBoxSizer’
mainwindow.cpp:52: error: ‘m_func_tabs’ was not declared in this scope
mainwindow.cpp:52: error: expected type-specifier before ‘wxListbook’
mainwindow.cpp:52: error: expected `;' before ‘wxListbook’
mainwindow.cpp:54: error: ‘m_func_tab_images’ was not declared in this scope
mainwindow.cpp:54: error: expected type-specifier before ‘wxImageList’
mainwindow.cpp:54: error: expected `;' before ‘wxImageList’
mainwindow.cpp:55: error: ‘chat_icon’ was not declared in this scope
mainwindow.cpp:55: error: ‘wxBITMAP’ was not declared in this scope
mainwindow.cpp:65: error: ‘SetSizer’ was not declared in this scope
mainwindow.cpp:67: error: ‘SetSize’ was not declared in this scope
mainwindow.cpp: In destructor ‘virtual MainWindow::~MainWindow()’:
mainwindow.cpp:74: error: ‘GetSize’ was not declared in this scope
mainwindow.cpp:77: error: ‘GetPosition’ was not declared in this scope
make[2]: *** [mainwindow.o] Error 1
make[2]: Leaving directory `/home/rutter/springlobby/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rutter/springlobby/trunk'
make: *** [all] Error 2 
```

[http://tc.serveftp.net/lobbydoc/index.html](http://tc.serveftp.net/lobbydoc/index.html)

---

### Post by Bachstelze on 2007-05-15
> Assuming you have wxWidgets installed...

Do you have it ?

---

### Post by Dr Small on 2007-05-15
Do you have build-essential installed?
```
sudo apt-get install build-essential
```

Dr Small

---

### Post by Hellcom on 2007-05-15
> **HymnToLife said:**
> Do you have it ?

I don't know, I can't find a package by this name in the respositories.

> **Dr Small said:**
> Do you have build-essential installed?
```
sudo apt-get install build-essential
```

Dr Small

Yes

---

### Post by Bachstelze on 2007-05-15
```
sudo apt-get install libwxgtk2.8-dev
```

---

### Post by Hellcom on 2007-05-15
> **HymnToLife said:**
> ```
sudo apt-get install libwxgtk2.8-dev
```

Says its already installed.

---

