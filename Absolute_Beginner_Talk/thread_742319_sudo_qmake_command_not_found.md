---
title: "sudo qmake command not found"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-04-01
right im tryin 2 install sopcast with instructions given here: [http://www.linux.ryukent.co.uk/show.php?id=36](http://www.linux.ryukent.co.uk/show.php?id=36)

im stuck at sudo qmake........i get: command not found....

any1 now how 2 handle this?

---

### Post by warp99 on 2008-04-01
Install this package:

```
sudo apt-get install qt3-dev-tools
```

---

### Post by Xiong Chiamiov on 2008-04-01
It seems to me from a quick google that you might have to build qmake from source.  [This]("http://ubuntuforums.org/showthread.php?t=231667") might be helpful.

---

### Post by t0p on 2008-04-01
> **Xiong Chiamiov said:**
> It seems to me from a quick google that you might have to build qmake from source.

Nah, there's no need to build qmake from source.  qmake is in the **qt3-dev-tools** package, which is in the repos.

---

### Post by Walc on 2008-04-01
ok i did install warp99's link
then i did manage to run sudo qmake
but heres what i got when running sudo make:

```

menubar.h:9: error: forward declaration of ‘struct QListViewItem’
make: *** [.obj/channel.o] Error 1
robert@lapek:/tmp/qsopcast-0.3.5/src$ sudo aptitude update
Get:1 http://pl.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://pl.archive.ubuntu.com gutsy-backports/main Translation-pl            
Ign http://pl.archive.ubuntu.com gutsy-backports/restricted Translation-pl      
Ign http://pl.archive.ubuntu.com gutsy-backports/universe Translation-pl        
Ign http://pl.archive.ubuntu.com gutsy-backports/multiverse Translation-pl      
Get:2 http://pl.archive.ubuntu.com gutsy Release.gpg [191B]                     
Hit http://pl.archive.ubuntu.com gutsy/main Translation-pl                      
Hit http://pl.archive.ubuntu.com gutsy/universe Translation-pl                  
Hit http://pl.archive.ubuntu.com gutsy/restricted Translation-pl                
Hit http://pl.archive.ubuntu.com gutsy/multiverse Translation-pl                
Get:3 http://www.virtualbox.org gutsy Release.gpg [189B]                        
Ign http://www.virtualbox.org gutsy/non-free Translation-pl                     
Get:4 http://pl.archive.ubuntu.com gutsy-updates Release.gpg [191B]             
Get:5 http://archive.canonical.com gutsy Release.gpg [191B]                     
Ign http://archive.canonical.com gutsy/partner Translation-pl                   
Get:6 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://security.ubuntu.com gutsy-security/universe Translation-pl           
Ign http://pl.archive.ubuntu.com gutsy-updates/universe Translation-pl          
Ign http://pl.archive.ubuntu.com gutsy-updates/main Translation-pl              
Ign http://pl.archive.ubuntu.com gutsy-updates/multiverse Translation-pl        
Ign http://pl.archive.ubuntu.com gutsy-updates/restricted Translation-pl        
Get:7 http://pl.archive.ubuntu.com gutsy-proposed Release.gpg [191B]            
Ign http://pl.archive.ubuntu.com gutsy-proposed/universe Translation-pl         
Ign http://pl.archive.ubuntu.com gutsy-proposed/main Translation-pl             
Ign http://pl.archive.ubuntu.com gutsy-proposed/multiverse Translation-pl       
Ign http://pl.archive.ubuntu.com gutsy-proposed/restricted Translation-pl       
Hit http://www.virtualbox.org gutsy Release                                     
Hit http://pl.archive.ubuntu.com gutsy-backports Release                        
Ign http://security.ubuntu.com gutsy-security/main Translation-pl               
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-pl         
Ign http://security.ubuntu.com gutsy-security/restricted Translation-pl         
Hit http://archive.canonical.com gutsy Release                                  
Hit http://security.ubuntu.com gutsy-security Release                           
Hit http://pl.archive.ubuntu.com gutsy Release                                  
Hit http://pl.archive.ubuntu.com gutsy-updates Release                          
Hit http://pl.archive.ubuntu.com gutsy-proposed Release                         
Hit http://pl.archive.ubuntu.com gutsy-backports/main Packages                  
Hit http://www.virtualbox.org gutsy/non-free Packages                           
Hit http://pl.archive.ubuntu.com gutsy-backports/restricted Packages            
Hit http://pl.archive.ubuntu.com gutsy-backports/universe Packages              
Hit http://pl.archive.ubuntu.com gutsy-backports/multiverse Packages            
Hit http://archive.canonical.com gutsy/partner Packages                         
Hit http://security.ubuntu.com gutsy-security/universe Packages                 
Hit http://pl.archive.ubuntu.com gutsy/main Packages                            
Hit http://pl.archive.ubuntu.com gutsy/universe Packages                        
Hit http://pl.archive.ubuntu.com gutsy/restricted Packages                      
Hit http://pl.archive.ubuntu.com gutsy/multiverse Packages           
Hit http://pl.archive.ubuntu.com gutsy-updates/universe Packages                
Hit http://pl.archive.ubuntu.com gutsy-updates/main Packages                    
Hit http://pl.archive.ubuntu.com gutsy-updates/multiverse Packages   
Hit http://pl.archive.ubuntu.com gutsy-updates/restricted Packages   
Hit http://pl.archive.ubuntu.com gutsy-proposed/universe Packages    
Hit http://pl.archive.ubuntu.com gutsy-proposed/main Packages        
Hit http://security.ubuntu.com gutsy-security/main Packages                     
Hit http://security.ubuntu.com gutsy-security/multiverse Packages               
Hit http://security.ubuntu.com gutsy-security/restricted Packages               
Hit http://pl.archive.ubuntu.com gutsy-proposed/multiverse Packages             
Hit http://pl.archive.ubuntu.com gutsy-proposed/restricted Packages  
Get:8 http://packages.medibuntu.org gutsy Release.gpg [189B]         
Ign http://packages.medibuntu.org gutsy/free Translation-pl
Ign http://packages.medibuntu.org gutsy/non-free Translation-pl
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 8B in 0s (9B/s)
Czytanie list pakietów... Gotowe
robert@lapek:/tmp/qsopcast-0.3.5/src$ sudo make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -I.moc/ -o .obj/channel.o channel.cpp
In file included from channel.cpp:21:
header.h:4:26: error: qapplication.h: No such file or directory
header.h:5:24: error: qtabwidget.h: No such file or directory
header.h:6:19: error: qvbox.h: No such file or directory
header.h:7:19: error: qhbox.h: No such file or directory
header.h:8:23: error: qlistview.h: No such file or directory
header.h:9:20: error: qlabel.h: No such file or directory
header.h:10:21: error: qslider.h: No such file or directory
header.h:11:25: error: qpushbutton.h: No such file or directory
header.h:12:23: error: qlineedit.h: No such file or directory
header.h:13:19: error: qhttp.h: No such file or directory
header.h:14:21: error: qbuffer.h: No such file or directory
header.h:15:21: error: qregexp.h: No such file or directory
header.h:16:22: error: qprocess.h: No such file or directory
header.h:17:24: error: qstatusbar.h: No such file or directory
header.h:18:20: error: qtimer.h: No such file or directory
header.h:19:23: error: qsettings.h: No such file or directory
header.h:20:22: error: qpalette.h: No such file or directory
header.h:21:29: error: qsocketnotifier.h: No such file or directory
header.h:22:21: error: qsocket.h: No such file or directory
header.h:23:22: error: qmenubar.h: No such file or directory
header.h:24:26: error: qradiobutton.h: No such file or directory
header.h:25:25: error: qmessagebox.h: No such file or directory
header.h:26:18: error: qdom.h: No such file or directory
header.h:27:25: error: qtoolbutton.h: No such file or directory
header.h:28:23: error: qptrlist.h: No such file or directory
In file included from channel.cpp:25:
config.h:4:21: error: qdialog.h: No such file or directory
channel.h:14: error: expected class-name before ‘{’ token
channel.h:15: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
channel.h:16: error: expected ‘;’ before ‘public’
channel.h:24: error: ISO C++ forbids declaration of ‘QValueList’ with no type
channel.h:24: error: expected ‘;’ before ‘<’ token
channel.h:25: error: ‘QString’ has not been declared
channel.h:25: error: ‘QString’ has not been declared
channel.h:25: error: ‘QString’ has not been declared
channel.h:28: error: ‘QMouseEvent’ has not been declared
channel.h:38: error: expected `:' before ‘slots’
channel.h:39: error: expected primary-expression before ‘void’
channel.h:39: error: ISO C++ forbids declaration of ‘slots’ with no type
channel.h:39: error: expected ‘;’ before ‘void’
channel.h:40: error: ‘QListViewItem’ has not been declared
channel.h:40: error: expected ‘,’ or ‘...’ before ‘&’ token
channel.h:40: error: ISO C++ forbids declaration of ‘QPoint’ with no type
channel.h:41: error: ‘QListViewItem’ has not been declared
channel.h:45: error: expected `:' before ‘slots’
channel.h:46: error: expected primary-expression before ‘void’
channel.h:46: error: ISO C++ forbids declaration of ‘slots’ with no type
channel.h:46: error: expected ‘;’ before ‘void’
mainwindow.h:20: error: expected class-name before ‘{’ token
mainwindow.h:21: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
mainwindow.h:22: error: expected ‘;’ before ‘public’
mainwindow.h:41: error: ‘QKeyEvent’ has not been declared
mainwindow.h:43: error: expected `:' before ‘slots’
mainwindow.h:44: error: expected primary-expression before ‘void’
mainwindow.h:44: error: ISO C++ forbids declaration of ‘slots’ with no type
mainwindow.h:44: error: expected ‘;’ before ‘void’
mylistitem.h:7: error: expected class-name before ‘{’ token
mylistitem.h:9: error: expected `)' before ‘*’ token
mylistitem.h:14: error: expected `)' before ‘*’ token
mylistitem.h:19: error: expected `)' before ‘*’ token
mylistitem.h:25: error: expected `)' before ‘*’ token
mylistitem.h:32: error: ‘QColor’ does not name a type
mylistitem.h:33: error: ‘QColor’ does not name a type
mylistitem.h:38: error: ‘QPainter’ has not been declared
mylistitem.h:38: error: expected ‘,’ or ‘...’ before ‘&’ token
mylistitem.h:39: error: ISO C++ forbids declaration of ‘QColorGroup’ with no type
mylistitem.h:56: error: ‘QListViewItem’ has not been declared
mylistitem.h: In member function ‘void MyListItem::paintCell(int*, int)’:
mylistitem.h:40: error: expected `;' before ‘_cg’
mylistitem.h:40: warning: statement has no effect
mylistitem.h:42: error: ‘_cg’ was not declared in this scope
mylistitem.h:42: error: ‘QColorGroup’ is not a class or namespace
mylistitem.h:42: error: ‘bcolor’ was not declared in this scope
mylistitem.h:43: error: ‘QColorGroup’ is not a class or namespace
mylistitem.h:43: error: ‘fcolor’ was not declared in this scope
mylistitem.h:45: error: ‘QListViewItem’ has not been declared
mylistitem.h:45: error: ‘column’ was not declared in this scope
mylistitem.h:45: error: ‘width’ was not declared in this scope
mylistitem.h:45: error: ‘alignment’ was not declared in this scope
mylistitem.h: In member function ‘int MyListItem::compare(int*, int, bool) const’:
mylistitem.h:64: error: ‘text’ was not declared in this scope
mylistitem.h:64: error: request for member ‘text’ in ‘* i’, which is of non-class type ‘int’
mylistitem.h:65: error: ‘QListViewItem’ has not been declared
config.h: At global scope:
config.h:9: error: expected class-name before ‘{’ token
config.h:10: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
config.h:11: error: expected ‘;’ before ‘public’
config.h:23: error: expected `:' before ‘slots’
config.h:24: error: expected primary-expression before ‘void’
config.h:24: error: ISO C++ forbids declaration of ‘slots’ with no type
config.h:24: error: expected ‘;’ before ‘void’
mylabel.h:8: error: invalid use of undefined type ‘struct QLabel’
config.h:7: error: forward declaration of ‘struct QLabel’
mylabel.h:10: error: expected `)' before ‘*’ token
mylabel.h:12: error: ‘QMouseEvent’ has not been declared
menubar.h:12: error: expected class-name before ‘{’ token
menubar.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
menubar.h:14: error: expected ‘;’ before ‘public’
menubar.h:29: error: expected `:' before ‘slots’
menubar.h:30: error: expected primary-expression before ‘void’
menubar.h:30: error: ISO C++ forbids declaration of ‘slots’ with no type
menubar.h:30: error: expected ‘;’ before ‘void’
menubar.h:32: error: expected `:' before ‘slots’
menubar.h:33: error: expected primary-expression before ‘void’
menubar.h:33: error: ISO C++ forbids declaration of ‘slots’ with no type
menubar.h:33: error: expected ‘;’ before ‘void’
./myhbox.h:9: error: expected class-name before ‘{’ token
./myhbox.h:11: error: expected `)' before ‘*’ token
./myhbox.h:16: error: ‘QString’ does not name a type
pageplay.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
pageplay.h:14: error: expected ‘;’ before ‘public’
pageplay.h:20: error: ‘QString’ does not name a type
pageplay.h:21: error: ‘QString’ does not name a type
pageplay.h:22: error: ‘QString’ does not name a type
pageplay.h:28: error: expected `:' before ‘slots’
pageplay.h:29: error: expected primary-expression before ‘void’
pageplay.h:29: error: ISO C++ forbids declaration of ‘slots’ with no type
pageplay.h:29: error: expected ‘;’ before ‘void’
pageplay.h:32: error: expected `:' before ‘slots’
pageplay.h:33: error: expected primary-expression before ‘void’
pageplay.h:33: error: ISO C++ forbids declaration of ‘slots’ with no type
pageplay.h:33: error: expected ‘;’ before ‘void’
record.h:16: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
record.h:17: error: expected ‘;’ before ‘public’
record.h:22: error: field ‘channelurl’ has incomplete type
record.h:23: error: field ‘channelname’ has incomplete type
record.h:24: error: field ‘channeltype’ has incomplete type
record.h:32: error: ISO C++ forbids declaration of ‘QTimer’ with no type
record.h:32: error: expected ‘;’ before ‘*’ token
record.h:33: error: ISO C++ forbids declaration of ‘QTimer’ with no type
record.h:33: error: expected ‘;’ before ‘*’ token
record.h:35: error: expected `:' before ‘slots’
record.h:36: error: expected primary-expression before ‘void’
record.h:36: error: ISO C++ forbids declaration of ‘slots’ with no type
record.h:36: error: expected ‘;’ before ‘void’
tabwidget.h:12: error: expected class-name before ‘{’ token
tabwidget.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
tabwidget.h:14: error: expected ‘;’ before ‘public’
tabwidget.h:17: error: ISO C++ forbids declaration of ‘QPtrList’ with no type
tabwidget.h:17: error: expected ‘;’ before ‘<’ token
tabwidget.h:18: error: ‘QWidget’ has not been declared
tabwidget.h:20: error: ‘QWidget’ has not been declared
tabwidget.h:26: error: ‘QMouseEvent’ has not been declared
tabwidget.h:28: error: expected `:' before ‘slots’
tabwidget.h:29: error: expected primary-expression before ‘void’
tabwidget.h:29: error: ISO C++ forbids declaration of ‘slots’ with no type
tabwidget.h:29: error: expected ‘;’ before ‘void’
tabwidget.h:33: error: ‘QWidget’ has not been declared
tabwidget.h:19: error: default argument for parameter of type ‘QString’ has type ‘const char [4]’
channel.cpp:35: error: expected `)' before ‘*’ token
channel.cpp: In destructor ‘Channel::~Channel()’:
channel.cpp:86: error: invalid use of undefined type ‘struct QBuffer’
channel.h:9: error: forward declaration of ‘struct QBuffer’
channel.cpp:87: warning: possible problem detected in invocation of delete operator:
channel.cpp:87: warning: invalid use of undefined type ‘struct QBuffer’
channel.h:9: warning: forward declaration of ‘struct QBuffer’
channel.cpp:87: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
channel.cpp: At global scope:
channel.cpp:93: error: no ‘void Channel::onListItemClicked(QListViewItem*)’ member function declared in class ‘Channel’
mainwindow.h: In member function ‘void Channel::onListItemClicked(QListViewItem*)’:
mainwindow.h:31: error: ‘TabWidget* MainWindow::tabwidget’ is private
channel.cpp:95: error: within this context
channel.cpp:95: error: ‘class TabWidget’ has no member named ‘currentPage’
mainwindow.h:31: error: ‘TabWidget* MainWindow::tabwidget’ is private
channel.cpp:97: error: within this context
channel.cpp:97: error: ‘class TabWidget’ has no member named ‘currentPage’
mainwindow.h:31: error: ‘TabWidget* MainWindow::tabwidget’ is private
channel.cpp:100: error: within this context
channel.cpp:100: error: ‘class TabWidget’ has no member named ‘currentPage’
channel.cpp: At global scope:
channel.cpp:107: error: no ‘void Channel::onButtonChannelToggled(bool)’ member function declared in class ‘Channel’
channel.cpp: In member function ‘void Channel::onButtonChannelToggled(bool)’:
channel.cpp:111: error: invalid use of undefined type ‘struct QBuffer’
channel.h:9: error: forward declaration of ‘struct QBuffer’
channel.cpp:113: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:114: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:115: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
mainwindow.h:30: error: ‘Config* MainWindow::vboxconfig’ is private
channel.cpp:115: error: within this context
config.h:17: error: ‘QLineEdit* Config::editchannelurl’ is private
channel.cpp:115: error: within this context
channel.cpp:115: error: invalid use of undefined type ‘struct QLineEdit’
mainwindow.h:7: error: forward declaration of ‘struct QLineEdit’
channel.cpp:116: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:117: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:118: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:123: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:124: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:125: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
mainwindow.h:25: error: ‘QToolButton* MainWindow::buttonchannel’ is private
channel.cpp:127: error: within this context
channel.cpp:127: error: invalid use of undefined type ‘struct QToolButton’
mainwindow.h:6: error: forward declaration of ‘struct QToolButton’
channel.cpp:127: error: ‘Qt’ has not been declared
channel.cpp: In member function ‘void Channel::wgetStdout()’:
channel.cpp:135: error: invalid use of undefined type ‘struct QBuffer’
channel.h:9: error: forward declaration of ‘struct QBuffer’
channel.cpp:135: error: invalid use of undefined type ‘struct QProcess’
channel.h:11: error: forward declaration of ‘struct QProcess’
channel.cpp:136: error: invalid use of undefined type ‘struct QBuffer’
channel.h:9: error: forward declaration of ‘struct QBuffer’
mainwindow.h:25: error: ‘QToolButton* MainWindow::buttonchannel’ is private
channel.cpp:142: error: within this context
channel.cpp:142: error: invalid use of undefined type ‘struct QToolButton’
mainwindow.h:6: error: forward declaration of ‘struct QToolButton’
channel.cpp:142: error: ‘QColor’ was not declared in this scope
mainwindow.h: In member function ‘void Channel::onWgetExit()’:
mainwindow.h:25: error: ‘QToolButton* MainWindow::buttonchannel’ is private
channel.cpp:151: error: within this context
channel.cpp:151: error: invalid use of undefined type ‘struct QToolButton’
mainwindow.h:6: error: forward declaration of ‘struct QToolButton’
channel.cpp:158: error: invalid use of undefined type ‘struct QBuffer’
channel.h:9: error: forward declaration of ‘struct QBuffer’
channel.cpp:159: error: ‘QDomDocument’ was not declared in this scope
channel.cpp:159: error: expected `;' before ‘doc’
channel.cpp:160: error: ‘doc’ was not declared in this scope
channel.cpp:167: error: ‘clear’ was not declared in this scope
channel.cpp:179: error: ‘QDomNode’ was not declared in this scope
channel.cpp:179: error: expected `;' before ‘group’
channel.cpp:180: error: ‘group’ was not declared in this scope
channel.cpp:182: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:183: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:185: error: expected `;' before ‘channelnode’
channel.cpp:186: error: ‘channelnode’ was not declared in this scope
channel.cpp:191: error: new initializer expression list treated as compound expression
channel.cpp:191: warning: left-hand operand of comma has no effect
channel.cpp:191: error: no matching function for call to ‘MyListItem::MyListItem(MyListItem*&)’
mylistitem.h:7: note: candidates are: MyListItem::MyListItem()
mylistitem.h:7: note:                 MyListItem::MyListItem(const MyListItem&)
channel.cpp:192: error: expected `;' before ‘namenode’
channel.cpp:193: error: ‘namenode’ was not declared in this scope
channel.cpp:196: error: ‘class MyListItem’ has no member named ‘setText’
channel.cpp:200: error: ‘class MyListItem’ has no member named ‘setText’
channel.cpp:209: error: ‘class MyListItem’ has no member named ‘text’
channel.cpp:218: error: ‘class MyListItem’ has no member named ‘text’
channel.cpp:219: error: ‘class MyListItem’ has no member named ‘text’
mainwindow.h:29: error: ‘MenuBar* MainWindow::menubar’ is private
channel.cpp:233: error: within this context
menubar.h:23: error: ‘int MenuBar::color_column’ is private
channel.cpp:233: error: within this context
channel.cpp:236: error: ‘firstChild’ was not declared in this scope
channel.cpp:237: error: ‘childCount’ was not declared in this scope
channel.cpp:237: error: ‘stateopen’ was not declared in this scope
channel.cpp:241: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:241: error: ‘TRUE’ was not declared in this scope
channel.cpp:242: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp: At global scope:
channel.cpp:249: error: expected ‘,’ or ‘...’ before ‘&’ token
channel.cpp:249: error: ISO C++ forbids declaration of ‘QPoint’ with no type
channel.cpp:249: error: prototype for ‘void Channel::onRightButtonClicked(QListViewItem*, int)’ does not match any in class ‘Channel’
channel.h:40: error: candidate is: void Channel::onRightButtonClicked(int*, int)
channel.cpp: In member function ‘void Channel::onRightButtonClicked(QListViewItem*, int)’:
channel.cpp:252: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:253: error: ‘class MyLabel’ has no member named ‘move’
channel.cpp:253: error: ‘pos’ was not declared in this scope
channel.cpp:255: error: ‘class MyLabel’ has no member named ‘setText’
channel.cpp:257: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:260: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:261: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:263: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:264: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:265: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:266: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:268: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:269: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:270: error: ‘class MyLabel’ has no member named ‘adjustSize’
channel.cpp:271: error: ‘class MyLabel’ has no member named ‘show’
channel.cpp: At global scope:
channel.cpp:249: warning: unused parameter ‘QPoint’
channel.cpp:277: error: prototype for ‘void Channel::onMouseMoved(QListViewItem*)’ does not match any in class ‘Channel’
channel.h:41: error: candidate is: void Channel::onMouseMoved(int*)
channel.cpp: In member function ‘void Channel::onMouseMoved(QListViewItem*)’:
channel.cpp:279: error: ‘class MyLabel’ has no member named ‘hide’
channel.cpp: At global scope:
channel.cpp:284: error: variable or field ‘mouseMoveEvent’ declared void
channel.cpp:284: error: ‘int Channel::mouseMoveEvent’ is not a static member of ‘class Channel’
channel.cpp:284: error: ‘QMouseEvent’ was not declared in this scope
channel.cpp:284: error: ‘e’ was not declared in this scope
channel.cpp:285: error: expected ‘,’ or ‘;’ before ‘{’ token
mainwindow.h: In member function ‘void Channel::toggleChannelSort()’:
mainwindow.h:29: error: ‘MenuBar* MainWindow::menubar’ is private
channel.cpp:303: error: within this context
menubar.h:21: error: ‘QPopupMenu* MenuBar::menu_config’ is private
channel.cpp:303: error: within this context
channel.cpp:303: error: invalid use of undefined type ‘struct QPopupMenu’
menubar.h:8: error: forward declaration of ‘struct QPopupMenu’
channel.cpp:304: error: ‘setSortColumn’ was not declared in this scope
channel.cpp:306: error: ‘setSortColumn’ was not declared in this scope
mainwindow.h: In member function ‘void Channel::toggleNullChannel()’:
mainwindow.h:29: error: ‘MenuBar* MainWindow::menubar’ is private
channel.cpp:313: error: within this context
menubar.h:21: error: ‘QPopupMenu* MenuBar::menu_config’ is private
channel.cpp:313: error: within this context
channel.cpp:313: error: invalid use of undefined type ‘struct QPopupMenu’
menubar.h:8: error: forward declaration of ‘struct QPopupMenu’
channel.cpp:315: error: ‘firstChild’ was not declared in this scope
channel.cpp:317: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:326: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:326: error: ‘FALSE’ was not declared in this scope
channel.cpp:328: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:328: error: ‘TRUE’ was not declared in this scope
channel.cpp:332: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:335: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:336: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:338: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:341: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:341: error: ‘FALSE’ was not declared in this scope
channel.cpp:343: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:343: error: ‘TRUE’ was not declared in this scope
channel.cpp:345: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp: In member function ‘void Channel::switchChannelColor(int)’:
channel.cpp:353: error: ‘firstChild’ was not declared in this scope
channel.cpp:355: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:357: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:359: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:364: error: ‘class MyListItem’ has no member named ‘fcolor’
channel.cpp:365: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:367: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:369: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp: In member function ‘void Channel::updateOpenState()’:
channel.cpp:377: error: ‘childCount’ was not declared in this scope
channel.cpp:377: error: ‘stateopen’ was not declared in this scope
channel.cpp:379: error: ‘firstChild’ was not declared in this scope
channel.cpp:382: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:387: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:392: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:397: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp: At global scope:
channel.cpp:405: error: prototype for ‘bool Channel::SopMatch(QString&, QString&, QString&)’ does not match any in class ‘Channel’
channel.h:25: error: candidate is: bool Channel::SopMatch(int&, int&, int&)
channel.cpp: In member function ‘bool Channel::SopMatch(QString&, QString&, QString&)’:
channel.cpp:407: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
channel.cpp:408: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
channel.cpp:411: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
mainwindow.h:30: error: ‘Config* MainWindow::vboxconfig’ is private
channel.cpp:411: error: within this context
config.h:18: error: ‘QLineEdit* Config::editchannelheader’ is private
channel.cpp:411: error: within this context
channel.cpp:411: error: invalid use of undefined type ‘struct QLineEdit’
mainwindow.h:7: error: forward declaration of ‘struct QLineEdit’
channel.cpp:416: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
channel.cpp:417: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
channel.cpp:417: error: invalid use of undefined type ‘struct QString’
record.h:10: error: forward declaration of ‘struct QString’
channel.cpp:421: error: ‘firstChild’ was not declared in this scope
channel.cpp:423: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:425: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:426: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:427: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:430: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
channel.cpp:432: error: invalid use of undefined type ‘struct QListViewItem’
menubar.h:9: error: forward declaration of ‘struct QListViewItem’
make: *** [.obj/channel.o] Error 1
robert@lapek:/tmp/qsopcast-0.3.5/src$ 

```

---

### Post by mc4man on 2008-04-01
ck and see if you have qt3-apps-dev and  libqt3-headers  (libqt3-headers recommends and replaces libqt3-mt-dev - I have both installed)

---

### Post by Walc on 2008-04-02
ck?

---

### Post by warp99 on 2008-04-02
You can check this way:

```
sudo apt-get install qt3-apps-dev libqt3-headers 
```

If they're installed you'll get a message stating so. If not apt-get will install them.

---

### Post by Walc on 2008-04-02
ok now i should go to 'setting up the gui'.
ive created menu shortcut. The thing is, its said i should be alble to run it from menu, but when im tryin 2, this is what i have: 
```

Couldnt launch menu item, 
failed to execute child process 'qsopcast' (no such file or directory)

```

---

### Post by Walc on 2008-04-02
bump?

---

### Post by Walc on 2008-04-03
final bump

---

