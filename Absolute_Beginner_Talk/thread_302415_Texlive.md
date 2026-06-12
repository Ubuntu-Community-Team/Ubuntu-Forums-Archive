---
title: "Texlive"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by snl on 2006-11-18
Which packages do I need from the repository to install texlive?

```
p   texlive                         - TeX Live: A decent selection of the TeX li
p   texlive-base                    - TeX Live: Essential programs and files    
p   texlive-base-bin                - TeX Live: Essential binaries              
p   texlive-bibtex-extra            - TeX Live: Extra BibTeX styles             
p   texlive-chemistry               - TeX Live: Chemical typesetting            
p   texlive-common                  - TeX Live: Base component                  
p   texlive-context                 - TeX Live: ConText macro package           
p   texlive-doc-base                - TeX Live: Base documentation              
p   texlive-doc-bg                  - TeX Live: Bulgarian documentation         
p   texlive-doc-cs+sk               - TeX Live: Czechslovak documentation       
p   texlive-doc-de                  - TeX Live: German documentation            
p   texlive-doc-el                  - TeX Live: Greek documentation             
p   texlive-doc-en                  - TeX Live: English documentation           
p   texlive-doc-es                  - TeX Live: Spanish documentation           
p   texlive-doc-fi                  - TeX Live: Finnish documentation           
p   texlive-doc-fr                  - TeX Live: French documentation            
p   texlive-doc-it                  - TeX Live: Italian documentation           
p   texlive-doc-ja                  - TeX Live: Japanese documentation          
p   texlive-doc-ko                  - TeX Live: Korean documentation            
p   texlive-doc-mn                  - TeX Live: Mongolian documentation         
p   texlive-doc-nl                  - TeX Live: Dutch documentation             
p   texlive-doc-pl                  - TeX Live: Polish documentation            
p   texlive-doc-pt                  - TeX Live: Portuguese documentation        
p   texlive-doc-ru                  - TeX Live: Russian documentation           
p   texlive-doc-th                  - TeX Live: Thai documentation              
p   texlive-doc-uk                  - TeX Live: Ukrainian documentation         
p   texlive-doc-vi                  - TeX Live: Vietnamese documentation        
p   texlive-extra-utils             - TeX Live: TeX auxiliary programs          
p   texlive-font-utils              - TeX Live: TeX font-related programs       
p   texlive-fonts-extra             - TeX Live: Extra fonts                     
p   texlive-fonts-recommended       - TeX Live: Recommended fonts               
p   texlive-formats-extra           - TeX Live: Extra formats                   
p   texlive-full                    - TeX Live: meta package pulling in all comp
p   texlive-games                   - TeX Live: Games typesetting (chess, etc)  
p   texlive-generic-extra           - TeX Live: Miscellaneous extra generic macr
p   texlive-generic-recommended     - TeX Live: Miscellaneous generic macros    
p   texlive-lang-african            - TeX Live: African scripts                 
p   texlive-lang-armenian           - TeX Live: Armenian                        
p   texlive-lang-croatian           - TeX Live: Croatian                        
p   texlive-lang-cyrillic           - TeX Live: Cyrillic                        
p   texlive-lang-czechslovak        - TeX Live: Czech/Slovak                    
p   texlive-lang-danish             - TeX Live: Danish                          
p   texlive-lang-dutch              - TeX Live: Dutch                           
p   texlive-lang-finnish            - TeX Live: Finnish                         
p   texlive-lang-french             - TeX Live: French                          
p   texlive-lang-german             - TeX Live: German                          
p   texlive-lang-greek              - TeX Live: Greek typesetting               
p   texlive-lang-hebrew             - TeX Live: Hebrew                          
p   texlive-lang-hungarian          - TeX Live: Hungarian                       
p   texlive-lang-indic              - TeX Live: Indic                           
p   texlive-lang-italian            - TeX Live: Italian                         
p   texlive-lang-latin              - TeX Live: Latin                           
p   texlive-lang-manju              - TeX Live: Manju                           
p   texlive-lang-mongolian          - TeX Live: Mongolian                       
p   texlive-lang-norwegian          - TeX Live: Norwegian                       
p   texlive-lang-other              - TeX Live: Other hyphenation files         
p   texlive-lang-polish             - TeX Live: Polish                          
p   texlive-lang-portuguese         - TeX Live: Portuguese                      
p   texlive-lang-spanish            - TeX Live: Spanish                         
p   texlive-lang-swedish            - TeX Live: Swedish                         
p   texlive-lang-tibetan            - TeX Live: Tibetan                         
p   texlive-lang-ukenglish          - TeX Live: UK English                      
p   texlive-lang-vietnamese         - TeX Live: Vietnamese                      
p   texlive-latex-base              - TeX Live: Basic LaTeX packages            
p   texlive-latex-extra             - TeX Live: LaTeX supplementary packages    
p   texlive-latex-recommended       - TeX Live: LaTeX recommended packages      
p   texlive-latex3                  - TeX Live: Experiment LaTeX3 packages      
p   texlive-math-extra              - TeX Live: Advanced math typesetting       
p   texlive-metapost                - TeX Live: MetaPost (and Metafont) drawing 
p   texlive-music                   - TeX Live: Music typesetting               
p   texlive-omega                   - TeX Live: Omega                           
p   texlive-pdfetex                 - TeX Live: pdfTeX                          
p   texlive-pictures                - TeX Live: Drawing and graphing packages   
p   texlive-plain-extra             - TeX Live: Plain TeX supplementary packages
p   texlive-pstricks                - TeX Live: PSTricks packages               
p   texlive-publishers              - TeX Live: Support for publishers       
```

Thank you.

---

### Post by snl on 2006-11-26
Could anyone help?

Do I need texlive-base or texlive-latex-base or both?

Thank you.

---

### Post by yugo on 2006-12-04
> **snl said:**
> Could anyone help?

Do I need texlive-base or texlive-latex-base or both?

Thank you.

texlive is a metapacket and will install all package required for a minimal installation.
I can see you use aptitude, so use aptitude show packageName

---

### Post by 7he on 2006-12-14
Yan also can install texlive-full. It's a metapackage that 'll install EVERYTHING you'll ever need when using texlive.
Caution, you 'll download 500 Mo of archives!

```
sudo aptget install texlive-full
```

Enjoy!
7he

---

