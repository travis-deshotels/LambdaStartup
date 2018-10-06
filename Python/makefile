my_zip = zipfile.zip
lambda_name = mylambda
aws_region = us-east-1

build:
	make requests

clean:
	rm -rf certifi* chardet* idna* urllib3* requests* $(my_zip)

deploy: $(my_zip)
	aws lambda update-function-code --function-name $(lambda_name) --zip-file fileb://$(my_zip) --region $(aws_region)

requests:
	pip3 install -r requirements.txt -t .

zip:
	make $(my_zip)

$(my_zip): mycode.py requests
	rm -f *.zip
	chmod -R a+rwx requests
	zip -r $(my_zip) mycode.py certifi chardet idna requests urllib3
