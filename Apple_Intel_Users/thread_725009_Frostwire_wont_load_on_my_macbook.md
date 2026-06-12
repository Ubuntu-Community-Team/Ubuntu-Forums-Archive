---
title: "Frostwire wont load on my macbook :/"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by PsyX on 2008-03-15
I dont know why it says limewire, but when i click the application i get this:

[IMG]http://i106.photobucket.com/albums/m260/mastermageex/Picture2.png[/IMG]

And then i looked at this:

[IMG]http://i106.photobucket.com/albums/m260/mastermageex/Picture1.png[/IMG]

I looked at the review and this is what i got.

LimeWire version 4.13.5
Java version 1.5.0_13 from Apple Inc.
Mac OS X v. 10.5.2 on i386
Free/total memory: 57362656/66650112

FATAL ERROR!

java.lang.OutOfMemoryError: Java heap space
	at java.lang.AbstractStringBuilder.expandCapacity(AbstractStringBuilder.java:99)
	at java.lang.AbstractStringBuilder.append(AbstractStringBuilder.java:575)
	at java.lang.StringBuilder.append(StringBuilder.java:204)
	at java.io.UnixFileSystem.resolve(UnixFileSystem.java:93)
	at java.io.File.<init>(File.java:284)
	at com.limegroup.gnutella.util.FileUtils.getFilesRecursive(FileUtils.java:395)
	at com.limegroup.gnutella.util.FileUtils.getLengthRecursive(FileUtils.java:564)
	at com.limegroup.gnutella.gui.library.LibraryTableDataLine.initialize(LibraryTableDataLine.java:259)
	at com.limegroup.gnutella.gui.library.LibraryTableDataLine.initialize(LibraryTableDataLine.java:44)
	at com.limegroup.gnutella.gui.tables.BasicDataLineModel.getNewDataLine(BasicDataLineModel.java:216)
	at com.limegroup.gnutella.gui.tables.BasicDataLineModel.add(BasicDataLineModel.java:275)
	at com.limegroup.gnutella.gui.library.LibraryTableModel.add(LibraryTableModel.java:63)
	at com.limegroup.gnutella.gui.library.LibraryTableModel.add(LibraryTableModel.java:20)
	at com.limegroup.gnutella.gui.tables.AbstractTableMediator.addUnsorted(AbstractTableMediator.java:501)
	at com.limegroup.gnutella.gui.library.LibraryTableMediator.updateTableFiles(LibraryTableMediator.java:439)
	at com.limegroup.gnutella.gui.library.LibraryMediator.updateTableFiles(LibraryMediator.java:289)
	at com.limegroup.gnutella.gui.library.LibraryTree$LibraryTreeSelectionListener.valueChanged(LibraryTree.java:631)
	at javax.swing.JTree.fireValueChanged(JTree.java:2399)
	at javax.swing.JTree$TreeSelectionRedirector.valueChanged(JTree.java:2770)
	at javax.swing.tree.DefaultTreeSelectionModel.fireValueChanged(DefaultTreeSelectionModel.java:629)
	at javax.swing.tree.DefaultTreeSelectionModel.notifyPathChange(DefaultTreeSelectionModel.java:1078)
	at javax.swing.tree.DefaultTreeSelectionModel.setSelectionPaths(DefaultTreeSelectionModel.java:287)
	at javax.swing.tree.DefaultTreeSelectionModel.setSelectionPath(DefaultTreeSelectionModel.java:170)
	at javax.swing.JTree.setSelectionPath(JTree.java:1174)
	at com.limegroup.gnutella.gui.library.LibraryTree.setInitialSelection(LibraryTree.java:242)
	at com.limegroup.gnutella.gui.library.LibraryMediator.<init>(LibraryMediator.java:136)
	at com.limegroup.gnutella.gui.library.LibraryMediator.<clinit>(LibraryMediator.java:85)
	at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:119)
	at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
	at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
	at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)

And i have no idea whats wrong, can someone tell me or help me?

Be honored if someone can help make this work :/.

---

### Post by cbiere on 2008-03-15
Do you use Ubuntu or Mac OS X?

---

### Post by PsyX on 2008-03-15
> **cbiere said:**
> Do you use Ubuntu or Mac OS X?

i use mac OS X

---

### Post by cyberdork33 on 2008-03-15
> **PsyX said:**
> i use mac OS X
Then why are you asking a linux forum?

---

### Post by ronocdh on 2008-03-15
This sure was bizarre.

---

