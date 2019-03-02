# latex_issue
1. matlab 生成 eps 格式的图没有嵌入字体，ieee 模板无法编译，[参考链接](https://sites.google.com/site/xyzliwen/resource/embed_font_ieee_pdf_explore)
> How to embed all fonts in your PDF file
> When you have one paper being accepted, the first thing is, CONGRATULATIONS! 
> 
> But next, you need to submit the camera-ready paper. Recently, a lot of conferences require that the camera-ready papers should be compatible with IEEE PDF eXplore. Usually, the conference will provide an account which allows you to submit your PDF file for compatible checking. A common problem is that some fonts are not embedded in the PDF file, which usually likes:
> 
>      Font Helvetica is not embedded (117x)
> 
> or some other fonts. One possible reason is that you used the EPS figure plotted with MATLAB in you paper. There're some fonts in the figure that are not included in your OS. 
> 
> Of course, we don't want to re-plot the figure with other fonts. I searched on the web and summarized a way to embed these fonts in your PDF file. With this method, you DO NOT need to modify your Latex file. You only need to convert some files to other format and then convert them back. OK, the ideas are as follows:
> - Convert your EPS figures to PDF (if your figure is PDF file, ignore this step). Use command:
>
> `epstopdf *.eps`
>
> - Embed fonts in your PDF figures. Use command:
> ```
> gswin32 -dSAFER -dNOPLATFONTS -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sPAPERSIZE=letter -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dCompatibilityLevel=1.4 -dMaxSubsetPct=100 -dSubsetFonts=true -dEmbedAllFonts=true -sOutputFile=temp.pdf -f *.pdf
> ```
>
> - Convert your PDF figure to EPS (Ignore this step if your figure is PDF file). Use command:
> ```
> pdftops -eps -level2 temp.pdf *.eps
> ```
>
> Copy the new EPS files to replace your original EPS files. Compile your Latex file again, and it's done!
