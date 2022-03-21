# meme
## My motivation for doing this meme is:
1. To practice my proficiency in R language.
2. To finish my **assignment1**.
3. I'm also interested in this, I hope to make more interesting pictures.
## At the same time I made some innovations：
* I used *two* images.
* I also *swapped the color of the text and background*.
* I also put the text on top.
I used R package [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html)
## my code:

<h1>example:</h1>



```{r}
library(magick)
picture1<- image_read("https://p1.ssl.qhimgs1.com/bdr/200_200_/t0115f01c975ced943d.jpg") %>%
  image_scale(500)

confused_cat <- image_read("https://p0.ssl.qhimgs4.com/t011625a36dc40eab59.jpg") %>%
  image_scale(500)

text1 <- image_blank(width = 500, 
                       height = 500, 
                       color = "#000000") %>%
  image_annotate(text = "The child in her own \neyes",
                 color = "#FFFFFF",
                 size = 45,
                 font = "Impact",
                 gravity = "center")

text2 <- image_blank(width = 500, 
                       height = 445, 
                       color = "#000000") %>%
  image_annotate(text = "What the others saw",
                 color = "#FFFFFF",
                 size = 45,
                 font = "Impact",
                 gravity = "center")

text3 <- image_blank(width = 1000, 
                       height = 200, 
                       color = "#FFFFFF") %>%
  image_annotate(text = '"You should see my baby, Look how cute she is."',
                 color = "#000000",
                 size = 45,
                 font = "Impact",
                 gravity = "center")

row1 <- c(text1,picture1) %>%
  image_append()

row2 <- c(text2,confused_cat) %>%
  image_append()

meme<-c(text3,row1, row2) %>%
  image_append(stack = TRUE)
image_write(meme, "my_meme.png")
```
