---
title: "Just installed Kubuntu 7.04 Feisty Fawn"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Dexter1337 on 2007-07-27
Well I just installed it I'm so happy everything is going so well. But I need to install flash but it gives me 3 options and I don't witch one to pick and I don't know how to get the root thing working in the terminal.

---

### Post by tomcheng76 on 2007-07-27
can you sudo ?
type this to terminal
sudo apt-get update
sudo apt-get install flashplugin-nonfree

---

### Post by NESFreak on 2007-07-27
> **tomcheng76 said:**
> can you sudo ?
type this to terminal
sudo apt-get update
sudo apt-get install flashplugin-nonfree

for that you need additional [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").
from the [flash wiki]("https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash#head-4b931137affcbddef2ac9102a3d9fafde91f869f"):
> 
Ubuntu 7.04 (Feisty Fawn)

    *

      Enable the Multiverse repository if you have not yet done so.
    *

      Due to a recent bug, you should probably also enable the "proposed updates" repository. See UbuntuUpdates. (This will no longer be necessary once the bug is fixed. See Troubleshooting below.)
    *

      Install the package flashplugin-nonfree.
    *

      Extra Step for Konqueror. In Konqueror, click Settings &#8594; Configure Konqueror. Scroll down the side to Plugins. Click Scan for new plugins
    *

      Restart your web browser. Flash should now work.

---

