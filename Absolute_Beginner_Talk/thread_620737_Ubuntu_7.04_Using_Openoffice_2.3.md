---
title: "Ubuntu 7.04 Using Openoffice 2.3"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by bleset on 2007-11-22
I am using ubuntu 7.04 and I want using openoffice 2.3 from ubuntu 7.10, not from native Openoffice.org, because i have problem using 7.10 in printing from java aplication, then i have to back using 7.04. Is it posible?  
I just try uninstall openoffice 2.2, and try to install openoffice from ubuntu 7.10 alternative, but not stable, i think because python-uno not install cause confict with older version(in installation process there is note).

Thank you.

---

### Post by runemaste644 on 2007-11-23
hmm... my only guess for what to do is to upgrade java...
Could you tell me what exactly it does?

---

### Post by bleset on 2007-11-28
> **runemaste644 said:**
> hmm... my only guess for what to do is to upgrade java...
Could you tell me what exactly it does?

Actually, i have been upgrade my java, using  java version "1.5.0_12". I cannot using java 1.6 because my application will not working.
I am using Adempiere(ERP/CRM) application. When I am using 7.04, everything going fine. The problems occur when, i have to use print dialog(print preview) in ubuntu 7.10, If not using print preview, every thing fine, sometimes I need use print preview, to set margin etc. I need to upgrade to openoffice 2.3 because in 2.2 some file that I have cannot be open in spreadsheet is not working perfect, and when i use native openoffice the auto filter not woriking perfectly ind spreadsheet. Honestly I am not sure, the problems comes from Ubuntu 7.10 or java printing dialog. I am not expert in java.

Im not sure the bug report is related to my problem or not but there is bug report.
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191)

Here is my error message.

-----------> ReportEngine.print: [COLOR="Blue"]Operating System Print Issue[/COLOR], check & try again [11]
java.lang.NullPointerException: null attribute
        at sun.print.IPPPrintService.isAttributeValueSupported(Unknown Source)
        at sun.print.ServiceDialog$OrientationPanel.updateInfo(Unknown Source)
        at sun.print.ServiceDialog$PageSetupPanel.updateInfo(Unknown Source)
        at sun.print.ServiceDialog.updatePanels(Unknown Source)
        at sun.print.ServiceDialog.initPrintDialog(Unknown Source)
        at sun.print.ServiceDialog.<init>(Unknown Source)
        at javax.print.ServiceUI.printDialog(Unknown Source)
        at sun.print.RasterPrinterJob.printDialog(Unknown Source)
        at org.compiere.print.ReportEngine.print(ReportEngine.java:298)
        at org.compiere.print.Viewer.cmd_print(Viewer.java:792)
        at org.compiere.print.Viewer.actionPerformed(Viewer.java:595)
        at javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
        at javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source)
        at javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
        at javax.swing.DefaultButtonModel.setPressed(Unknown Source)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source)
        at java.awt.AWTEventMulticaster.mouseReleased(Unknown Source)
        at java.awt.Component.processMouseEvent(Unknown Source)
        at javax.swing.JComponent.processMouseEvent(Unknown Source)
        at java.awt.Component.processEvent(Unknown Source)
        at java.awt.Container.processEvent(Unknown Source)

---

