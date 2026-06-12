---
title: "amule aborts immediately"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by adssse on 2006-08-17
I just installed amule today, but when I start it it almost immediately aborts. I started it from the terminal to see what messages it gave me and here they are:

===================================================

Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/adssse/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /cdrom/ shared
        aMule Version: aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded)

Terminated after throwing an instance of 'CSeekFailureException'
        what(): SafeIO::IOFailure::SeekFailure: Failed to retrieve length of fil e: Invalid argument
        backtrace:
[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x8081acc]
[3] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb76a4a8d]
[4] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb76a4af8]
[5] CryptoPP::IteratedHashBase2<unsigned int, CryptoPP::EnumToType<CryptoPP::Byt eOrder, 0>, CryptoPP::HashTransformation>::~IteratedHashBase2() in amule [0x8127 6cc]
[6] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb7419ea2]
[7] __gxx_personality_v0 in amule[0x807dad1]

Aborted

======================================================

I also tried completely removing amule and amule-common with purging and reinstalling, but I get the same result. Any help would be appreciated.

---

