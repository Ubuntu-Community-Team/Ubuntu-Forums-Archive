---
title: "qtopia installation issues"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ramandeep on 2008-02-08
Hello,
        I am new to Linux development and I have no idea how to get around this. Kindly help me out.

I installed qtopia on my system through an rpm named    qtopia-free-1.7.0-2rh9.i386.rpm.
now when i try to compile a sample code hello2.cpp with the following contents:

#include <qtopia/qpeapplication.h>
int main(int argc, char **argv)
{
QPEApplication a(argc, argv);

return a.exec();
}

I get  the following error:

[root@localhost bin]# ./arm-linux-g++ -I /opt/Qtopia/sharp/include/ -DQWS -fno-rtti -o hello2.o -c hello2.cpp
[root@localhost bin]# ./arm-linux-g++ -L /opt/Qtopia/sharp/lib/ -o hello2 hello2.o -lqte -lqpe -ljpeg -luuid
hello2.o(.text+0x6c): In function `main':
: undefined reference to `QPEApplication::QPEApplication[in-charge](int&, char**, QApplication::Type)'
hello2.o(.text+0xa4): In function `main':
: undefined reference to `QMainWindow::QMainWindow[in-charge](QWidget*, char const*, unsigned)'
hello2.o(.text+0xfc): In function `main':
: undefined reference to `QString::QString[in-charge](char const*)'
hello2.o(.text+0x1a8): In function `main':
: undefined reference to `QPEApplication::showMainWidget(QWidget*, bool)'
hello2.o(.text+0x1b4): In function `main':
: undefined reference to `QPEApplication::exec()'
hello2.o(.text+0x1cc): In function `main':
: undefined reference to `QPEApplication::~QPEApplication [in-charge]()'
hello2.o(.text+0x1f4): In function `main':
: undefined reference to `QPEApplication::~QPEApplication [in-charge]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0xc): undefined reference to `QGList::clear()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x10): undefined reference to `QGList::~QGList [in-charge]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x14): undefined reference to `QGList::~QGList [in-charge deleting]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x18): undefined reference to `QCollection::newItem(void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x1c): undefined reference to `QCollection::deleteItem(void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x20): undefined reference to `QGList::compareItems(void*, void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x24): undefined reference to `QGList::read(QDataStream&, void*&)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x28): undefined reference to `QGList::write(QDataStream&, void*) const'
hello2.o(.gnu.linkonce.t._ZN7QStringD1Ev+0x64): In function `QString::~QString [in-charge]()':
: undefined reference to `QStringData::deleteSelf()'
hello2.o(.gnu.linkonce.t._ZN7QStringD1Ev+0x70): In function `QString::~QString [in-charge]()':
: undefined reference to `QString::shared_null'
collect2: ld returned 1 exit status
[root@localhost bin]# ./arm-linux-g++ -I /opt/Qtopia/sharp/include/ -DQWS -fno-rtti -o hello2.o -c hello2.cpp
[root@localhost bin]# ./arm-linux-g++ -L /opt/Qtopia/sharp/lib/ -o hello2 hello2.o -lqte -lqpe -ljpeg -luuid
hello2.o(.text+0x6c): In function `main':
: undefined reference to `QPEApplication::QPEApplication[in-charge](int&, char**, QApplication::Type)'
hello2.o(.text+0x80): In function `main':
: undefined reference to `QPEApplication::exec()'
hello2.o(.text+0x98): In function `main':
: undefined reference to `QPEApplication::~QPEApplication [in-charge]()'
hello2.o(.text+0xcc): In function `main':
: undefined reference to `QPEApplication::~QPEApplication [in-charge]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0xc): undefined reference to `QGList::clear()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x10): undefined reference to `QGList::~QGList [in-charge]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x14): undefined reference to `QGList::~QGList [in-charge deleting]()'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x18): undefined reference to `QCollection::newItem(void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x1c): undefined reference to `QCollection::deleteItem(void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x20): undefined reference to `QGList::compareItems(void*, void*)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x24): undefined reference to `QGList::read(QDataStream&, void*&)'
hello2.o(.gnu.linkonce.r._ZTV6QGList+0x28): undefined reference to `QGList::write(QDataStream&, void*) const'
collect2: ld returned 1 exit status

I am using Fedora 6 and compiling for arm target  board running on Linux.I want to use qt/embedded for displaying graphics on a TFT LCD connected to arm9 board.

thanks,
ramandeep
contact email: [email]ramandeeps@cimcon.com[/email]

---

### Post by Byapti on 2008-02-25
Hi,

I think the Qtopia article on [http://www.linuxdevices.com/articles/AT7319394180.html]("http://www.linuxdevices.com/articles/AT7319394180.html") may be helpful in this discussion.

This popular white paper is written by some engineering folks from our organization Mindfire Solutions ([http://www.mindfiresolutions.com]("http://www.mindfiresolutions.com")).

I hope you find it useful!

Cheers,
Byapti

---

