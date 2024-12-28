FROM python:3.10-slim  AS build
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY  . /app/
CMD ["python","app.py"]

FROM python:3.10-slim  AS production

WORKDIR /app

COPY --from=build /app ./dist
COPY --from=build /app/requirements.txt ./

RUN pip install -r requirements.txt

EXPOSE 5000

ENTRYPOINT ["python","dist/app.py"]





