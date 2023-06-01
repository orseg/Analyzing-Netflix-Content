# Analyzing Netflix Content - Exploratory Data Analysis
Using Netflix Dataset and Python

-   Libraries used: pyplot from matplotlib, pandas.

-   IDE used: Spyder

-   Dataset used: [Netflix Movies and TV Shows from
    Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows)

**Technical Stuff:**

First and foremost, importing pandas and matplotlib.pyplot

And read the csv to new dataframe.

```python
import pandas as pd
import matplotlib.pyplot as plt

netflix = pd.read_csv('netflix_titles.csv')
```

Next step is cleansing, there are few empty values, so I\'ll fill them
with ```unknown```.

```python
netflix.fillna(value="unknown", inplace = True) # fill NaNs with unknown
```

The dataframe looks something like this --



**Let's start!**

## **Distribution of Genres**

![](media/image4.png){width="7.643055555555556in"
height="3.785744750656168in"}

![תמונה שמכילה טקסט, צילום מסך, תרשים, מקביל התיאור נוצר באופן
אוטומטי](media/image5.png){width="7.780555555555556in"
height="3.8541666666666665in"}

As we can see from the graphs above, Most of Netflix content is
International Movies and TV Shows. More than 2500 titles are
International Movies, and more than 700 titles are International TV
Shows.

Seems like International titles are on high demand.

On the last 2 graphs there is the number of titles in each type. 6131
Movies and 2676 TV Shows. This data corresponds to the next Pie chart
that shows that most of the content in Netflix are movies with 69.6% and
30.4% are TV Shows.

![](media/image6.png){width="3.4023523622047245in"
height="3.2079319772528434in"}

+-----------------------------------------------------------------------+
| [\# Distribution of genres]{.mark}                                    |
|                                                                       |
| [netflix**\[**\"genres\"**\]** **=**                                  |
| netflix**\[**\"listed_in\"**\].str.**split**(**\',\'**)** \# new      |
| column for genres]{.mark}                                             |
|                                                                       |
| [all_genres **=** **\[\]**]{.mark}                                    |
|                                                                       |
| [**for** genres **in** netflix**\[**\"genres\"**\]:**]{.mark}         |
|                                                                       |
| [**for** genre **in** genres**:**]{.mark}                             |
|                                                                       |
| [all_genres**.**append**(**genre**)**]{.mark}                         |
|                                                                       |
| [genre_counts **=**                                                   |
| pd**.**Series**(**all_genres**).**value_counts**()**]{.mark}          |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))** \# increase size of  |
| the plot]{.mark}                                                      |
|                                                                       |
| [genre_counts**.**plot**(**kind**=**\'bar\'**)**]{.mark}              |
|                                                                       |
| [plt**.**xlabel**(**\'Genre\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Distribution of Genres\'**)**]{.mark}            |
|                                                                       |
| [plt**.**xticks**(**rotation**=**\'vertical\'**)**]{.mark}            |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [#\-- Distribution of genres for movies and tv shows]{.mark}          |
|                                                                       |
| [\# MOVIES]{.mark}                                                    |
|                                                                       |
| [all_movies **=**                                                     |
| netflix**\[**                                                         |
| netflix**\[**\'type\'**\].str.**contains**(**\"Movie\"**)\]**]{.mark} |
|                                                                       |
| [movie_genres **=** **\[**genre **for** genres **in**                 |
| all_movies**\[**\"genres\"**\]** **for** genre **in**                 |
| genres**\]**]{.mark}                                                  |
|                                                                       |
| [movie_genre_counts **=**                                             |
| pd**.**Series**(**movie_genres**).**value_counts**()**]{.mark}        |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))** \# increase size of  |
| the plot]{.mark}                                                      |
|                                                                       |
| [movie_genre_counts**.**plot**(**kind**=**\'bar\'**)**]{.mark}        |
|                                                                       |
| [plt**.**xlabel**(**\'Genre\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Distribution of Movie Genres\'**)**]{.mark}      |
|                                                                       |
| [plt**.**xticks**(**rotation**=**\'vertical\'**)**]{.mark}            |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt_text_movies **=** f\"{**len(**movie_genre_counts**)**} Movie     |
| genres and {**len(**all_movies**)**} Movies overall\"]{.mark}         |
|                                                                       |
| [plt**.**text**(len(**movie_genre_counts**)/**2**,** 1500**,**        |
| plt_text_movies**,** color**=**\'black\'**,** fontsize**=**10**,**    |
| ha**=**\'center\'**)**]{.mark}                                        |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# TV SHOWS]{.mark}                                                  |
|                                                                       |
| [all_tvshows **=**                                                    |
| netflix**\[**netflix**\[**\'type\'**\].str.**contains**(**\"TV        |
| Show\"**)\]**]{.mark}                                                 |
|                                                                       |
| [tvshow_genres **=** **\[**genre **for** genres **in**                |
| all_tvshows**\[**\"genres\"**\]** **for** genre **in**                |
| genres**\]**]{.mark}                                                  |
|                                                                       |
| [tvshow_genre_counts **=**                                            |
| pd**.**Series**(**tvshow_genres**).**value_counts**()**]{.mark}       |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))** \# increase size of  |
| the plot]{.mark}                                                      |
|                                                                       |
| [tvshow_genre_counts**.**plot**(**kind**=**\'bar\'**)**]{.mark}       |
|                                                                       |
| [plt**.**xlabel**(**\'Genre\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Distribution of TV Shows Genres\'**)**]{.mark}   |
|                                                                       |
| [plt**.**xticks**(**rotation**=**\'vertical\'**)**]{.mark}            |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt_text_tvshows **=** f\"{**len(**tvshow_genre_counts**)**} TV Show |
| genres and {**len(**all_tvshows**)**} TV Shows overall\"]{.mark}      |
|                                                                       |
| [plt**.**text**(len(**tvshow_genre_counts**)/**2**,** 500**,**        |
| plt_text_tvshows**,** color**=**\'black\'**,** fontsize**=**10**,**   |
| ha**=**\'center\'**)**]{.mark}                                        |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# Movies vs TV Shows]{.mark}                                        |
|                                                                       |
| [type_counts **=**                                                    |
| pd**                                                                  |
| .**Series**(**netflix**\[**\"type\"**\]).**value_counts**()**]{.mark} |
|                                                                       |
| [type_counts**                                                        |
| .**plot**(**kind**=**\'pie\'**,**autopct**=**\'%1.1f%%\'**)**]{.mark} |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

-   **Country of Origin**

![](media/image7.png){width="2.50034886264217in"
height="2.958746719160105in"}

In the first place we can see that US is dominating with 3690 titles and
India in second place with 1046 titles.

Let\'s take the top 5 countries and put them in a horizontal bar plot.

![](media/image8.png){width="6.054798775153106in"
height="3.4440135608048994in"}

Let\'s take a further look at the US for example:

![תמונה שמכילה טקסט, צילום מסך, גופן, תרשים התיאור נוצר באופן
אוטומטי](media/image9.png){width="3.3745778652668417in"
height="3.4301268591426073in"}

We can see that 75% of the titles from the US are movies, 2752 titles to
be exact and only 25% of the titles are tv shows (938 titles).

+-----------------------------------------------------------------------+
| [\## Country of origin]{.mark}                                        |
|                                                                       |
| [netflix**\[**\"countries\"**\]** **=**                               |
| netflix**\[**\"country\"**\].str.**split**(**\',\'**)**]{.mark}       |
|                                                                       |
| [all_countries **=** **\[**country **for** countries **in**           |
| netflix**\[**\"countries\"**\]** **for** country **in**               |
| countries**\]**]{.mark}                                               |
|                                                                       |
| [all_countries **=** **\[**country**.**lstrip**()** **for** country   |
| **in** all_countries**\]** \# remove unnecessary space from the start |
| of values]{.mark}                                                     |
|                                                                       |
| [country_counts **=**                                                 |
| pd**.**Series**(**all_countries**).**value_counts**()**]{.mark}       |
|                                                                       |
| [country_counts **=**                                                 |
| country_counts**.**drop**(**labels**=\[**\'unknown\'**\])** \# drop   |
| unknown values]{.mark}                                                |
|                                                                       |
| [\# Top 5 countries in horizontal bar plot]{.mark}                    |
|                                                                       |
| [country_counts**.**head**(**5**).**plot**(**kind**=**\'barh\'**,**   |
| color**=**\'purple\'**,**                                             |
| orientation**=**\"horizontal\"**).**invert_yaxis**()**]{.mark}        |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# Tv Shows and Movies from the US]{.mark}                           |
|                                                                       |
| [us_tvshows **=**                                                     |
| netflix**\[(**netflix**\[**\'type\'**\].str.**contains**(**\"TV       |
| Show\"**))** **&**                                                    |
| **(**netflix**\[**\'country\'**\].str.**contains**(**\"United         |
| States\"**))\]**]{.mark}                                              |
|                                                                       |
| [us_movies **=**                                                      |
| netfl                                                                 |
| ix**\[(**netflix**\[**\'type\'**\].str.**contains**(**\"Movie\"**))** |
| **&** **(**netflix**\[**\'country\'**\].str.**contains**(**\"United   |
| States\"**))\]**]{.mark}                                              |
|                                                                       |
| [us_tvshows_count **=** **len(**us_tvshows**)**]{.mark}               |
|                                                                       |
| [us_movies_count **=** **len(**us_movies**)**]{.mark}                 |
|                                                                       |
| [us_pie_lables **=** **\[**\'TV Shows\'**,** \'Movies\'**\]**]{.mark} |
|                                                                       |
| [us_pie_data **=** **\[**us_tvshows_count**,**                        |
| us_movies_count**\]**]{.mark}                                         |
|                                                                       |
| [plt**.**pie**(**us_pie_data**,**labels**=**us_pie_lables**,**        |
| colors**=\[**\'#ff9999\'**,** \'#66b3ff\'**\],**                      |
| explode**=(**0.1**,**0**),** shadow**=True,**                         |
| autopct**=**\'%1.0f%%\'**)**]{.mark}                                  |
|                                                                       |
| [**for** i**,** size **in** **enumerate(**us_pie_data**):**]{.mark}   |
|                                                                       |
| [percentage_label **=** f\"{size}                                     |
| ({us_pie_data**\[**i**\]/sum(**us_pie_data**)\***100:.0f}%)\"]{.mark} |
|                                                                       |
| [plt**.**text**(**i**,** **-**1.2**,** percentage_label**,**          |
| color**=**\'black\'**,** fontsize**=**10**,**                         |
| ha**=**\'center\'**)**]{.mark}                                        |
|                                                                       |
| [plt**.**title**(**\'Tv Shows and Movies from the US\'**)**]{.mark}   |
+=======================================================================+
+-----------------------------------------------------------------------+

-   **Distribution of Ratings**

![](media/image10.png){width="6.134413823272091in"
height="3.0384864391951005in"}

More than 3000 titles are marked as TV-MA rating which means that big
portion of the titles in Netflix is mature content which the audience
seems to like very much. In the next graph we\'ll see the progression.

+-----------------------------------------------------------------------+
| [\# Distribution of ratings]{.mark}                                   |
|                                                                       |
| [rating_counts **=**                                                  |
| pd**.*                                                                |
| *Series**(**netflix**\[**\'rating\'**\]).**value_counts**()**]{.mark} |
|                                                                       |
| [rating_counts **=**                                                  |
| rating_counts**.**drop**(**labels**=\[**\'unknown\'**,**\'74          |
| min\'**,**\'84 min\'**,** \'66 min\'**\])** \# dropping duration time |
| values which don\'t belong to rating and dropping unknown             |
| values.]{.mark}                                                       |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,**6**))**]{.mark}               |
|                                                                       |
| [rating_counts**.**plot**(**kind**=**\'bar\'**,**                     |
| color**=**\'red\'**)**]{.mark}                                        |
|                                                                       |
| [plt**.**xlabel**(**\'Rating\'**)**]{.mark}                           |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Distribution of Ratings\'**)**]{.mark}           |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

-   **Content added Over the Years**

![](media/image11.png){width="5.4854254155730535in"
height="4.207807305336833in"}

By this graph we can see that over the years TV-MA rating titles become
very popular since 2017 and are requested a lot. Also, we can see that
2019 was the year with the highest content added.

In addition, 2019 was the year with the highest number of movies and tv
shows added.

![](media/image12.png){width="5.4854254155730535in"
height="4.207807305336833in"}

+-----------------------------------------------------------------------+
| [\## CONTECT ADDED OVER THE YEARS]{.mark}                             |
|                                                                       |
| [netflix**\[**\'date_added\'**\].**replace**(**\'unknown\'**,**       |
| pd**.**NaT**,** inplace**=True)**]{.mark}                             |
|                                                                       |
| [netflix**\[**\'date_added\'**\]** **=**                              |
| netflix**\[**\'date_added\'**\].str.**strip**()**]{.mark}             |
|                                                                       |
| [netflix**\[**\'date_added\'**\]** **=**                              |
| pd**.**to_datetime**(**netflix**\[**\'date_added\'**\],**             |
| **format=**\'%B %d, %Y\'**)**]{.mark}                                 |
|                                                                       |
| [netflix**\[**\'year_added\'**\]** **=**                              |
| netflix**\[**\'date_added\'**\].**dt**.**year]{.mark}                 |
|                                                                       |
| [\# Progress of Ratings Over the Years]{.mark}                        |
|                                                                       |
| [ratings_to_exclude **=** **\[**\'unknown\'**,**\'74 min\'**,**\'84   |
| min\'**,** \'66 min\'**\]** \# unknown and duration time values were  |
| excluded from rating.]{.mark}                                         |
|                                                                       |
| [filtered_df **=**                                                    |
| netflix**\                                                            |
| [\~**netflix**\[**\'rating\'**\].**isin**(**ratings_to_exclude**)\]** |
| \# filtered dataframe without them.]{.mark}                           |
|                                                                       |
| [rating_counts **=**                                                  |
| filtered_df**.**groupby**(\[**\'year_added\'**,**                     |
| \                                                                     |
| 'rating\'**\]).**size**().**unstack**(**fill_value**=**0**)**]{.mark} |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))**]{.mark}              |
|                                                                       |
| [rating_counts**.**plot**(**kind**=**\'bar\'**,**                     |
| stacked**=True)**]{.mark}                                             |
|                                                                       |
| [plt**.**xlabel**(**\'Year Added\'**)**]{.mark}                       |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Progress of Ratings Over the                     |
| Years\'**)**]{.mark}                                                  |
|                                                                       |
| [plt**.**legend**(**title**=**\'Rating\'**)**]{.mark}                 |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# Difference of content added over the years]{.mark}                |
|                                                                       |
| [content_counts **=** netflix**.**groupby**(\[**\'year_added\'**,**   |
| \'type\'**\]).**size**().**unstack**(**fill_value**=**0**)**]{.mark}  |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))**]{.mark}              |
|                                                                       |
| [content_counts**.**plot**(**kind**=**\'bar\'**,**                    |
| stacked**=True)**]{.mark}                                             |
|                                                                       |
| [plt**.**xlabel**(**\'Year Added\'**)**]{.mark}                       |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Progress of Content Over the                     |
| Years\'**)**]{.mark}                                                  |
|                                                                       |
| [plt**.**legend**(**title**=**\'Type\'**)**]{.mark}                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

-   **Overall Content Added Over the Months**

![](media/image13.png){width="5.4854254155730535in"
height="3.8606288276465444in"}

Looks like that near the end of the year is the time when Netflix adds
new content and lots of them!

+-----------------------------------------------------------------------+
| [\# Overall Content Added Over the Months]{.mark}                     |
|                                                                       |
| [netflix**\[**\'month_added\'**\]** **=**                             |
| netflix**\[**\'date_added\'**\].**dt**.**month]{.mark}                |
|                                                                       |
| [plt**.**hist**(**x**=**\"month_added\"**,**data**=**netflix**,**     |
| edgecolor**=**\'k\'**,** rwidth**=**0.5**)**]{.mark}                  |
|                                                                       |
| [plt**.**xlabel**(**\'Month\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\"Count\"**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Overall Content Added Over the                   |
| Months\'**)**]{.mark}                                                 |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

-   ![](media/image14.png){width="7.715277777777778in"
    height="3.8208333333333333in"}**Distribution of Seasons of TV
    Shows**

> Looks like that every tv show has at least one season which is obvious
> but a tv show to have more than one season become very rare. Close to
> 1750 titles have one season but only approx. 500 titles got 2 seasons.

+-----------------------------------------------------------------------+
| [\# Distribution of Seasons of TV Shows]{.mark}                       |
|                                                                       |
| [tvshows_only **=**                                                   |
| netflix**\[**netflix**\[**\'type\'**\].str.**contains**(**\"TV        |
| Show\"**)\]**]{.mark}                                                 |
|                                                                       |
| [tvshows_season_count **=**                                           |
| pd**.**Series                                                         |
| **(**tvshows_only**\[**\'duration\'**\]).**value_counts**()**]{.mark} |
|                                                                       |
| [plt**.**figure**(**figsize**=(**12**,** 6**))** \# increase size of  |
| the plot]{.mark}                                                      |
|                                                                       |
| [tvshows_season_count**.**plot**(**kind**=**\'bar\'**)**]{.mark}      |
|                                                                       |
| [plt**.**xlabel**(**\'Seasons\'**)**]{.mark}                          |
|                                                                       |
| [plt**.**ylabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**title**(**\'Distribution of Seasons of TV                    |
| Shows\'**)**]{.mark}                                                  |
|                                                                       |
| [plt**.**xticks**(**rotation**=**\'vertical\'**)**]{.mark}            |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

-   **Top Directors for Movies and TV Shows**

> ![](media/image15.png){width="5.30445428696413in"
> height="3.5029418197725284in"}
>
> ![תמונה שמכילה טקסט, צילום מסך, גופן, מספר התיאור נוצר באופן
> אוטומטי](media/image16.png){width="5.045858486439195in"
> height="3.332169728783902in"}
>
> ![תמונה שמכילה טקסט, צילום מסך, גופן, מספר התיאור נוצר באופן
> אוטומטי](media/image17.png){width="4.64156605424322in"
> height="3.0651848206474193in"}
>
> As shown in the graphs, Rajiv made more than 20 titles overall. Rajiv
> is also in the first place in the Top 15 Movies Directors. Alastair is
> in the first place in Top 15 TV Shows Directors with 3 titles.

+-----------------------------------------------------------------------+
| [\## Top Directors for Movies and TV Shows]{.mark}                    |
|                                                                       |
| [\# Top 15 Overall]{.mark}                                            |
|                                                                       |
| [netflix**\[**\"directors\"**\]** **=**                               |
| netflix**\[**\"director\"**\].str.**split**(**\',\'**)**]{.mark}      |
|                                                                       |
| [all_directors **=** **\[**director **for** directors **in**          |
| netflix**\[**\"directors\"**\]** **for** director **in**              |
| directors**\]**]{.mark}                                               |
|                                                                       |
| [all_directors **=** **\[**director**.**lstrip**()** **for** director |
| **in** all_directors**\]** \# remove unnecessary space from the start |
| of values]{.mark}                                                     |
|                                                                       |
| [director_counts **=**                                                |
| pd**.**Series**(**all_directors**).**value_counts**()**]{.mark}       |
|                                                                       |
| [director_counts **=**                                                |
| director_counts**.**drop**(**labels**=\[**\'unknown\'**\])** \# drop  |
| unknown values]{.mark}                                                |
|                                                                       |
| [director_counts**.**head**                                           |
| (**15**).**plot**(**kind**=**\'barh\'**).**invert_yaxis**()**]{.mark} |
|                                                                       |
| [plt**.**xlabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Director\'**)**]{.mark}                         |
|                                                                       |
| [plt**.**title**(**\'Top 15 Directors Overall\'**)**]{.mark}          |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# Top 15 Movies]{.mark}                                             |
|                                                                       |
| [only_movies_directors **=**                                          |
| netfl                                                                 |
| ix**\[(**netflix**\[**\'type\'**\].str.**contains**(**\"Movie\"**))** |
| **&**                                                                 |
| **(**n                                                                |
| etflix**\[**\'director\'**\].**isin**(**all_directors**))\]**]{.mark} |
|                                                                       |
| [movies_directors_counts **=**                                        |
| pd**.**Series**(**only                                                |
| _movies_directors**\[**\'director\'**\]).**value_counts**()**]{.mark} |
|                                                                       |
| [movies_directors_counts **=**                                        |
| movies_                                                               |
| directors_counts**.**drop**(**labels**=\[**\'unknown\'**\])**]{.mark} |
|                                                                       |
| [movies_directors_counts**.**head**                                   |
| (**15**).**plot**(**kind**=**\'barh\'**).**invert_yaxis**()**]{.mark} |
|                                                                       |
| [plt**.**xlabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Director\'**)**]{.mark}                         |
|                                                                       |
| [plt**.**title**(**\'Top 15 Movies Directors\'**)**]{.mark}           |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
|                                                                       |
| [\# Top 15 TV Shows]{.mark}                                           |
|                                                                       |
| [only_tv_directors **=**                                              |
| netflix**\[(**netflix**\[**\'type\'**\].str.**contains**(**\"TV       |
| Show\"**))** **&**                                                    |
| **(**n                                                                |
| etflix**\[**\'director\'**\].**isin**(**all_directors**))\]**]{.mark} |
|                                                                       |
| [tv_directors_counts **=**                                            |
| pd**.**Series**(**                                                    |
| only_tv_directors**\[**\'director\'**\]).**value_counts**()**]{.mark} |
|                                                                       |
| [tv_directors_counts **=**                                            |
| tv_                                                                   |
| directors_counts**.**drop**(**labels**=\[**\'unknown\'**\])**]{.mark} |
|                                                                       |
| [tv_directors_counts**.**head**                                       |
| (**15**).**plot**(**kind**=**\'barh\'**).**invert_yaxis**()**]{.mark} |
|                                                                       |
| [plt**.**xlabel**(**\'Count\'**)**]{.mark}                            |
|                                                                       |
| [plt**.**ylabel**(**\'Director\'**)**]{.mark}                         |
|                                                                       |
| [plt**.**title**(**\'Top 15 TV Shows Directors\'**)**]{.mark}         |
|                                                                       |
| [plt**.**tight_layout**()**]{.mark}                                   |
|                                                                       |
| [plt**.**show**()**]{.mark}                                           |
+=======================================================================+
+-----------------------------------------------------------------------+

**\
**

**Conclusions**

As we saw in this exploratory data analysis --

-   Movies playing a big part in Netflix\'s content.

-   The vast majority of the content is international.

-   Most of the titles coming from United States.

-   most of the title are mature rated (TV-MA).

-   Netflix likes to add new content when we reach the end of the year.

-   Not all TV shows get to see another season.
