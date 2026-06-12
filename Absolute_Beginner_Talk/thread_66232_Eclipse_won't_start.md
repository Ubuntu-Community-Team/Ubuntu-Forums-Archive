---
title: "Eclipse won't start"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by KwikStah on 2005-09-16
EDIT: Never mind, I got it working...

I'm running Breezy, here's what I get from the logs, any idea?

!SESSION 2005-09-16 08:48:33.710 -----------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Debian 4.0.1-4ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.update.configurator 2005-09-16 08:48:34.929
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2005-09-16 08:48:35.481
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (22).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins/org.eclipse.osgi_3.1.0.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (/usr/lib/eclipse/plugins/org.eclipse.osgi_3.1.0.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (/usr/lib/eclipse/plugins/org.eclipse.osgi_3.1.0.jar.so)

---

