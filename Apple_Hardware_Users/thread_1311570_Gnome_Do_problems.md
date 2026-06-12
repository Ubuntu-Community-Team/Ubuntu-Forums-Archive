---
title: "Gnome Do problems"
date: 2009-11-02
forum: Apple Hardware Users
---

### Post by ricky0319 on 2009-11-02
I just installed 9.10 on my Macbook 2,1. First I want to say this is by far the best release and I am loving karmic. I just have a problem with Gnome Do. I have installed Gnome Do and it does not open. When I click on it nothing happens. I have tried deleting several times and reinstalling it still nothing. I have tried from the software center, synaptic and a .deb file. Any suggestions?

When I try to run gnome do in the terminal this what happens -

ERROR: Unexpected error in setup process
System.Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.InternalScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
  at Mono.Addins.Database.AddinDatabase.ScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
ERROR: Add-in scan operation failed
Stack overflow in unmanaged: IP: 0x81a64ec, fault addr: 0xbf4edffc
ERROR: The add-in database could not be updated. It may be due to file corruption. Try running the setup repair utility

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Do.Platform.Services.Initialize () [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 


I am still new at linux and I am not sure what all this is.

---

