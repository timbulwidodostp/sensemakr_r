# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# provide suite of sensitivity analysis tools for Ordinary Least Square (OLS) Use sensemakr With R Software
install.packages("readxl")
install.packages("httr")
install.packages("sensemakr")
library(httr)
library("readxl")
library("sensemakr")
# Import Data Excel Into R From Github Olah Data Semarang (timbulwidodostp)
github_link <- "https://github.com/timbulwidodostp/sensemakr_r/raw/main/sensemakr_r/sensemakr_r.xlsx"
temp_file <- tempfile(fileext = ".xlsx")
req <- GET(github_link, 
# authenticate using GITHUB_PAT
authenticate(Sys.getenv("GITHUB_PAT"), ""),
# write result to disk
write_disk(path = temp_file))
sensemakr_r <- readxl::read_excel(temp_file)
# Estimate provide suite of sensitivity analysis tools for Ordinary Least Square (OLS) Use sensemakr With R Software
sensemakr_r_model<-lm(peacefactor~directlyharmed+village+female+age+farmer_dar+herder_dar+pastvoted+hhsize_darfur,data=sensemakr_r)
sensemakr_r_sensitivity<-sensemakr(model=sensemakr_r_model,treatment="directlyharmed",benchmark_covariates="female",kd=1:3,ky=1:3,q=1,alpha=0.05,reduce=TRUE)
summary(sensemakr_r_sensitivity)
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished
